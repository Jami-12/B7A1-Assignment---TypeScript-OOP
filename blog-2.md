# TypeScript: Why `unknown` is the Safer Choice Over `any`

## Introduction
TypeScript-এর মূল উদ্দেশ্য হলো টাইপ সেফটি নিশ্চিত করা। কিন্তু অনেক সময় ডেভেলপাররা অজান্তেই `any` ব্যবহার করে একটি "Type Safety Hole" তৈরি করেন। এই ব্লগে আমরা আলোচনা করবো কেন `any` ঝুঁকিপূর্ণ এবং কীভাবে `unknown` ও **Type Narrowing** ব্যবহারের মাধ্যমে আমরা আরও নিরাপদ কোড লিখতে পারি।

---

## The Danger of `any`
`any` টাইপ মূলত TypeScript-এর কম্পাইলারকে ওই ভেরিয়েবলের উপর সব ধরণের চেকিং বন্ধ করতে বলে। এটি টাইপ সিস্টেমকে পুরোপুরি বাইপাস করে দেয়, ফলে রানটাইমে ক্র্যাশ করার সম্ভাবনা থাকে।

### The Runtime Crash Example:
```typescript
let myData: any = "Hello Jami";

// TypeScript will not complain here, but it will fail at runtime
myData.push(10); // Error: myData.push is not a function
The Safer Alternative: unknownunknown টাইপও যেকোনো ভ্যালু গ্রহণ করতে পারে, কিন্তু এটি ব্যবহার করার আগে TypeScript আপনাকে টাইপ চেক করতে বাধ্য করবে। এটিই হলো এর প্রধান নিরাপত্তা।Type Narrowing in Actionunknown ভ্যালুকে ব্যবহারযোগ্য করার প্রক্রিয়াকে বলা হয় Type Narrowing।TypeScriptlet userInput: unknown;

userInput = "Professional Web Development";

// Error: Object is of type 'unknown'
// console.log(userInput.toUpperCase()); 

// Correct Way (Type Narrowing)
if (typeof userInput === "string") {
  console.log(userInput.toUpperCase()); // Now it's safe!
}
Comparison TableFeatureanyunknownType Safety None HighUsageDirectly usableMust be narrowedRisk💣 High Risk🛡️ Safe ChoiceConclusionany ব্যবহার করা মানে হলো টাইপ সিস্টেমের সুবিধাকে অগ্রাহ্য করা। অন্যদিকে unknown ডেভেলপারকে দায়িত্বশীল কোড লিখতে বাধ্য করে। তাই প্রোজেক্টে আনপ্রেডিক্টেবল ডেটা হ্যান্ডেল করার জন্য সবসময় unknown ব্যবহার করা এবং প্রপার টাইপ ন্যারোইং করা উচিত।