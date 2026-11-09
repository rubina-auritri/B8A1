Type Narrowing in TypeScript



\## Introduction

Type Narrowing হলো runtime-এ কোনো value পরীক্ষা করে TypeScript-কে বোঝানো যে নির্দিষ্ট condition-এর মধ্যে variable-টি কোন type-এর।



\## Detailed Explanation

TypeScript-এ একটি variable-এর মধ্যে একাধিক ধরনের value থাকতে পারে। যেমন:

let value: string | number;

এখানে value-এর মধ্যে string অথবা number থাকতে পারে।



কিন্তু আমরা যদি সরাসরি value.toUpperCase() ব্যবহার করি, তাহলে সমস্যা হবে। কারণ number-এর মধ্যে toUpperCase() method নেই।



এই সমস্যা সমাধানের জন্য Type Narrowing ব্যবহার করা হয়।



Type Narrowing হলো runtime-এ কোনো value পরীক্ষা করে TypeScript-কে বোঝানো যে নির্দিষ্ট condition-এর মধ্যে variable-টি কোন type-এর।



typeof Operator:

typeof ব্যবহার করে primitive data type পরীক্ষা করা যায়।



যেমন:

\- string

\- number

\- boolean

\- undefined

\- bigint

\- symbol



function format(value: string | number): string {

&#x20; if (typeof value === "string") {

&#x20;   return value.toUpperCase();

&#x20; }



&#x20; return value.toFixed(2);

}



instanceof Operator:

instanceof ব্যবহার করা হয় কোনো object নির্দিষ্ট class-এর instance কি না পরীক্ষা করার জন্য।



class Dog {

&#x20; bark() {

&#x20;   return "Woof!";

&#x20; }

}



function makeSound(pet: Dog | Date): string {

&#x20; if (pet instanceof Dog) {

&#x20;   return pet.bark();

&#x20; }



&#x20; return pet.toDateString();

}





in Operator

in operator ব্যবহার করে কোনো object-এর মধ্যে নির্দিষ্ট property আছে কি না পরীক্ষা করা হয়।



যখন Union Type-এর object-গুলোর property আলাদা থাকে, তখন এটি খুব কাজে লাগে।



type Admin = {

&#x20; name: string;

&#x20; permissions: string\[];

};



type Customer = {

&#x20; name: string;

&#x20; purchaseCount: number;

};



function describe(user: Admin | Customer) {

&#x20; if ("permissions" in user) {

&#x20;   return user.permissions.join(", ");

&#x20; }



&#x20; return `Purchases: ${user.purchaseCount}`;

}



\## Conclusion

Type Narrowing-এর মাধ্যমে TypeScript-এর runtime checking এবং compile-time safety একসঙ্গে কাজ করে।

\- Primitive data type পরীক্ষা করার জন্য typeof ব্যবহার করা হয়।

\- কোনো object নির্দিষ্ট class-এর instance কি না পরীক্ষা করতে instanceof ব্যবহার করা হয়।

\- কোনো object-এর মধ্যে নির্দিষ্ট property আছে কি না পরীক্ষা করতে in ব্যবহার করা হয়।

এই তিনটি operator Union Type নিয়ে কাজ করার সময় কোডকে আরও পরিষ্কার ও নিরাপদ করে। পাশাপাশি অপ্রয়োজনীয় Type Assertion (as) ব্যবহার কমাতে সাহায্য করে।

