# TypeScript Generics: Reusable and Type-Safe Code

---

## Introduction

TypeScript-এ Generics ব্যবহার করা হয় এমন কোড লেখার জন্য যা বিভিন্ন ধরনের ডেটা টাইপ হ্যান্ডেল করতে পারে, কিন্তু টাইপ সেফটি (Type Safety) বজায় রাখে। বড় প্রোজেক্টে একই ফাংশন বা কম্পোনেন্ট বারবার বিভিন্ন টাইপের জন্য ব্যবহার করার ক্ষেত্রে এটি অত্যন্ত কার্যকর।

---

## What are Generics?

Generics হলো এমন একটি ফিচার যেখানে আমরা Type-কে একটি ভেরিয়েবলের মতো ব্যবহার করি। এটি কোনো নির্দিষ্ট টাইপ লক না করে রানটাইমে বা কল করার সময় টাইপ নির্ধারণ করার সুযোগ দেয়।

---

### Example

```ts
function identity<T>(value: T): T {
  return value;
}

এখানে <T> একটি প্লেসহোল্ডার, যা যেকোনো টাইপ যেমন string, number বা object হতে পারে।

Example Usage
console.log(identity<string>("Hello")); // Output: Hello
console.log(identity<number>(100));     // Output: 100
Why Generics is Useful?
Without Generics (Unsafe Approach)

যদি আমরা any ব্যবহার করি, তবে টাইপ সেফটি হারিয়ে যায় এবং ভুল ডেটা আসার সম্ভাবনা থাকে।

function getData(value: any): any {
  return value;
}
With Generics (Safe Approach)

Generics ব্যবহারের ফলে TypeScript নিশ্চিত করে যে সঠিক টাইপ ব্যবহার হচ্ছে।

function getData<T>(value: T): T {
  return value;
}
Real-world Example

অ্যারে তৈরির ক্ষেত্রে Generics-এর একটি বাস্তব উদাহরণ:

function makeArray<T>(items: T[]): T[] {
  return items;
}

const strArray = makeArray<string>(["A", "B", "C"]);
const numArray = makeArray<number>([10, 20, 30]);
Conclusion

TypeScript-এ Generics ব্যবহারের প্রধান সুবিধাগুলো হলো:

কোডকে Reusable করে
Type Safety নিশ্চিত করে
বড় প্রোজেক্টকে আরও Maintainable করে তোলে

তাই Generics TypeScript development এর একটি খুব গুরুত্বপূর্ণ concept।