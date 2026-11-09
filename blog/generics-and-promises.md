TypeScript Generics এবং Promise<T>: পুনরায় ব্যবহারযোগ্য ও Type-Safe Asynchronous Code

Introduction
Generics ব্যবহার করে TypeScript-এ এমন Function, Interface অথবা Class তৈরি করা যায়, যেগুলো বিভিন্ন Data Type নিয়ে কাজ করতে পারে এবং একই সঙ্গে Type Information ধরে রাখতে পারে।

সাধারণত any ব্যবহার করলে TypeScript-এর Type Checking অনেকটা বন্ধ হয়ে যায়। কিন্তু Generic ব্যবহার করলে একটি Type সংরক্ষণ করা যায় এবং পুরো Operation জুড়ে সেই Type বজায় রাখা যায়।

বিশেষ করে Asynchronous Code-এর ক্ষেত্রে এটি অনেক গুরুত্বপূর্ণ। কারণ, একটি Promise ভবিষ্যতে কোনো একটি নির্দিষ্ট Data বা Result Return করে।

## Detailed Explanation
১. Generic Function কী?
একটি Generic Function তৈরি করার সময় আমরা একটি Type Parameter ব্যবহার করি। সাধারণত এই Type Parameter-এর নাম T রাখা হয়।

Function Call করার সময় আমরা চাইলে সরাসরি Type নির্ধারণ করতে পারি। আবার Function-এর Argument দেখে TypeScript নিজে থেকেই Type বুঝে নিতে পারে। একে Type Inference বলে।
function identity<T>(value: T): T {
  return value;
}

const message = identity<string>("Hello");
const count = identity(42); // TypeScript নিজেই number বুঝে নেয়



২. Promise<T> কী?
Promise<T> ব্যবহার করে বোঝানো হয় যে একটি Promise ভবিষ্যতে নির্দিষ্ট Type-এর একটি Value Return করবে।

ধরুন, আমরা কোনো API থেকে একজন User-এর Information নিয়ে আসতে চাই।

প্রথমে User-এর Data Structure নির্ধারণ করি।
type User = {
  id: number;
  name: string;
};

async function getUser(): Promise<User> {
  const response = await fetch("/api/users/1");

  if (!response.ok) {
    throw new Error("Could not load user");
  }

  return (await response.json()) as User;
}

৩. Generic Function এবং Promise<T> একসঙ্গে ব্যবহার
আমরা চাইলে এমন একটি Generic API Function তৈরি করতে পারি, যেটি বিভিন্ন ধরনের Data নিয়ে কাজ করতে পারবে।
async function fetchData<T>(url: string): Promise<T> {
  const response = await fetch(url);

  if (!response.ok) {
    throw new Error("Request failed");
  }

  return (await response.json()) as T;
}

const user = await fetchData<User>("/api/users/1");

## Conclusion
Generics ব্যবহার করলে একই Code বিভিন্ন Data Type-এর জন্য পুনরায় ব্যবহার করা যায়, Type Safety নষ্ট না করেই।

অন্যদিকে, Promise<T> ব্যবহার করে বোঝানো যায় যে একটি Asynchronous Function ভবিষ্যতে নির্দিষ্ট Type-এর Data Return করবে।

এই দুটি একসঙ্গে ব্যবহার করলে Reusable, Flexible এবং Type-Safe Asynchronous Code লেখা অনেক সহজ হয়।