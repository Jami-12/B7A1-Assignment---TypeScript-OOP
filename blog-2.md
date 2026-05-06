# TypeScript: any vs unknown – Why unknown is the Safer Choice

---

## 1. Introduction

TypeScript এ type safety খুব গুরুত্বপূর্ণ। কিন্তু অনেক সময় আমরা ভুল করে `any` ব্যবহার করি, যা পুরো type safety system নষ্ট করে দেয়। এই সমস্যার সমাধান হিসেবে `unknown` একটি safer alternative।

এই blog এ আমরা বুঝবো কেন `any` dangerous এবং কেন `unknown` better choice।

---

## 2. What is `any`?

`any` মানে হলো TypeScript কোনো type checking করবে না।

### Example:

```ts id="any1"
let data: any;

data = "Hello";
data = 10;
data = true;

এখানে যেকোনো কিছু assign করা যাচ্ছে
 TypeScript কোনো error দিচ্ছে না

Problem with any
let value: any = "Hello";

value.toUpperCase(); // OK
value.push(10);      // No error (but runtime crash possible)

এখানে ভুল method ব্যবহার করলেও TypeScript ধরতে পারে না
এটা dangerous

3. What is unknown?

unknown মানে হলো আমরা জানি না data কি type, কিন্তু ব্যবহার করার আগে check করতে হবে।

Example:
let data: unknown;

data = "Hello";
data = 42;
data = true;
4. Why unknown is safer?
Wrong usage (will give error)
let value: unknown = "Hello";

value.toUpperCase(); // Error
Correct usage (type narrowing)
let value: unknown = "Hello";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}

এখানে আমরা আগে type check করছি
এটাকে বলে type narrowing

5. Type Narrowing Explanation

Type narrowing মানে হলো variable এর actual type confirm করা before using it.

Example:

function printData(data: unknown) {
  if (typeof data === "number") {
    console.log(data.toFixed(2));
  }

  if (typeof data === "string") {
    console.log(data.toUpperCase());
  }
}
6. Difference between any and unknown
Feature	any	unknown
Type Safety	 No	- Yes
Error Checking	 No	- Yes
Risk	High	Low
Best Practice	Not recommended	Recommended
7. Conclusion

any পুরো type system bypass করে, যা বড় bug তৈরি করতে পারে।
unknown safer কারণ এটি ব্যবহার করার আগে type check করতে বাধ্য করে।

Final Advice:

Always prefer unknown over any in TypeScript projects.