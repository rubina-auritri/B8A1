Type Alias vs Interface in TypeScript

## Introduction 
TypeScript-এ type এবং interface দুটোই ব্যবহার করা হয় কোনো Data Structure  নির্ধারণ করার জন্য।

বিশেষ করে কোনো Object-এর মধ্যে কী কী Property থাকবে এবং সেগুলোর Data Type কী হবে, তা নির্ধারণ করতে আমরা এগুলো ব্যবহার করি।

দেখতে অনেকটা একই রকম হলেও এদের মধ্যে কিছু পার্থক্য রয়েছে।

## Detailed Explanation

interface মূলত কোনো Object-এর গঠন বা Structure নির্ধারণ করতে ব্যবহার করা হয়।

অর্থাৎ, একটি Object-এর মধ্যে কী কী Property থাকবে, তা Interface দিয়ে বলে দেওয়া যায়।

উদাহরণ:

interface User {
  id: number;
  name: string;
}
Interface-এর একটি বিশেষ সুবিধা হলো extends ব্যবহার করে অন্য Interface-এর Property নেওয়া যায়।

interface User {
  id: number;
  name: string;
}

interface Admin extends User {
  permissions: string[];
}

এখন Admin Object তৈরি করি:
const admin: Admin = {
  id: 1,
  name: "Rubina",
  permissions: ["create", "edit", "delete"]
};

Interface-এর আরেকটি বিশেষ সুবিধা: Declaration Merging
একই নামের Interface একাধিকবার তৈরি করলে TypeScript সেগুলোকে একসঙ্গে Merge করে দেয়।

উদাহরণ:
interface User {
  id: number;
  name: string;
}

interface User {
  email: string;
}
এখন TypeScript এই দুটি Interface-কে একসঙ্গে ধরে নেবে।

অর্থাৎ, User-এর মধ্যে থাকবে:
interface User {
  id: number;
  name: string;
  email: string;
}

Type Alias
type ব্যবহার করেও আমরা Object-এর Structure নির্ধারণ করতে পারি।

type User = {
  id: number;
  name: string;
  এটিও Interface-এর মতোই কাজ করছে।
  type-এর বিশেষ সুবিধা হলো এটি শুধু Object নয়, আরও বিভিন্ন ধরনের Type তৈরি করতে পারে।
};
যেমন:
১. Union Type (|)

একটি Variable একাধিক নির্দিষ্ট Type-এর যেকোনো একটি গ্রহণ করতে পারবে।
type Status = "pending" | "success" | "failed";

২. Primitive Type
type Age = number;

type Name = string;

৩. Tuple Type
type Point = [number, number];

const location: Point = [10, 20];

৪. Intersection Type (&)

দুই বা তার বেশি Type একসঙ্গে যুক্ত করতে পারি।

type User = {
  name: string;
};

type Admin = {
  role: string;
};

type AdminUser = User & Admin;
const admin: AdminUser = {
  name: "Rubina",
  role: "admin"
};
## Conclusion
দুটোই Object-এর Structure নির্ধারণ করতে পারে। প্রয়োজন অনুযায়ী ব্যবহার করতে হবে। তবে একই Project-এ একটি নির্দিষ্ট Coding Style অনুসরণ করা ভালো।