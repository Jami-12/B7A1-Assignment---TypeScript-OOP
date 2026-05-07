# Master TypeScript Utility Types: Pick and Omit

## Introduction
বড় প্রোজেক্টে কাজ করার সময় আমরা প্রায়ই দেখি যে একটি বড় Interface-এর ছোট কিছু অংশ আমাদের দরকার হয়। বারবার নতুন টাইপ লেখা মানেই কোড ডুপ্লিকেশন। এই সমস্যা সমাধানে TypeScript আমাদের দেয় **Pick** এবং **Omit** এর মতো পাওয়ারফুল ইউটিলিটি টাইপস। এগুলো আমাদের কোডকে **DRY (Don't Repeat Yourself)** রাখতে সাহায্য করে।

---

## 1. Using `Pick` to Slice Interfaces
যখন আমাদের একটি বড় ইন্টারফেস থেকে মাত্র কয়েকটি স্পেসিফিক প্রোপার্টি দরকার হয়, তখন আমরা `Pick` ব্যবহার করি।

### Example:
```typescript
interface User {
  id: string;
  username: string;
  email: string;
  avatarUrl: string;
  lastLogin: Date;
}

// Creating a specialized slice for profile card
type UserProfileBase = Pick<User, "username" | "avatarUrl">;

const profile: UserProfileBase = {
  username: "Mujaddid Ahmed Jami",
  avatarUrl: "[https://example.com/jami.jpg](https://example.com/jami.jpg)"
};
2. Using Omit to Filter Interfaces
Omit ঠিক Pick-এর উল্টো কাজ করে। এটি কোনো ইন্টারফেস থেকে নির্দিষ্ট কিছু প্রোপার্টি বাদ দিয়ে নতুন টাইপ তৈরি করে। এটি বিশেষ করে সেনসিটিভ ডেটা (যেমন পাসওয়ার্ড) বাদ দিতে কার্যকর।

Example:
TypeScript
interface Employee {
  id: number;
  name: string;
  department: string;
  salary: number; // Sensitive data
}

// Creating a public version of employee info
type PublicEmployeeInfo = Omit<Employee, "salary">;

const info: PublicEmployeeInfo = {
  id: 101,
  name: "Ahmed",
  department: "Development"
};
Why These Types are Essential?
Prevents Duplication: প্রতিবার নতুন টাইপ না লিখে বেস ইন্টারফেস থেকেই নতুন ভার্সন তৈরি করা যায়।

Easy Maintenance: যদি মূল ইন্টারফেসে কোনো চেঞ্জ হয়, তবে Pick বা Omit করা টাইপগুলো অটোমেটিক আপডেট হয়ে যায়।

Improves Clarity: কোড দেখে সহজেই বোঝা যায় কোন ডেটা কোথায় ব্যবহার হচ্ছে।

Conclusion
Pick এবং Omit হলো ক্লিন কোড লেখার জাদুকরী হাতিয়ার। এগুলো ব্যবহারের মাধ্যমে আপনি একটি মাস্টার ইন্টারফেস থেকেই বিভিন্ন স্পেশালাইজড টাইপ তৈরি করতে পারেন, যা আপনার প্রোজেক্টকে করে তুলবে আরও স্মার্ট এবং মেইনটেইনেবল।