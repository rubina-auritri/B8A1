# TypeScript-এ any, unknown এবং never কী?



##  Introduction

TypeScript-এ কিছু বিশেষ Type আছে, যেগুলো নির্ধারণ করে একটি Value কীভাবে ব্যবহার করা যাবে। এর মধ্যে গুরুত্বপূর্ণ তিনটি Type হলো any, unknown এবং never।



এগুলোর কাজ আলাদা। কোনটি কখন ব্যবহার করতে হবে, তা জানা থাকলে আমাদের Code আরও নিরাপদ এবং সহজে Maintain করা যায়।

## Detailed Explanation

১. any Type

any ব্যবহার করলে TypeScript-এর Type Checking অনেকটাই বন্ধ হয়ে যায়।



অর্থাৎ, একটি Variable-এ যেকোনো ধরনের Value রাখা যায় এবং সেই Value-এর যেকোনো Property বা Method ব্যবহার করা যায়। TypeScript তখন সাধারণত কোনো Error দেখায় না।



let value: any = "hello";



value.toFixed();

এখানে value একটি String। কিন্তু আমরা এর ওপর toFixed() Method ব্যবহার করেছি, যা Number-এর জন্য।



TypeScript any থাকার কারণে কোনো Error দেখাবে না। কিন্তু Code Run করলে Error হবে।



২. unknown Type

unknown-এর মাধ্যমে যেকোনো ধরনের Value রাখা যায়। তবে any-এর মতো সরাসরি সেই Value ব্যবহার করা যায় না।



ব্যবহারের আগে Value-টির Type Check করতে হয়।



উদাহরণ:

function printLength(value: unknown) {

 if (typeof value === "string") {

   console.log(value.length);

 }

}



এখানে:

. value-এর Type হলো unknown।

. typeof value === "string" দিয়ে পরীক্ষা করা হয়েছে Value-টি String কি না।

. String হলে তার length ব্যবহার করা হয়েছে।

অর্থাৎ, আগে Type Check করতে হবে, তারপর Value ব্যবহার করতে হবে।



৩. never Type

never এমন একটি Type, যার মাধ্যমে বোঝানো হয় কোনো Value কখনোই তৈরি হতে পারে না।



সাধারণত এমন Function-এর ক্ষেত্রে never ব্যবহার করা হয়, যেগুলো সবসময় Error Throw করে অথবা কখনোই শেষ হয় না।



উদাহরণ:

function fail(message: string): never {

 throw new Error(message);

}

এখানে Function-টি সবসময় Error Throw করে। তাই এটি কোনো Value Return করে না। এজন্য এর Return Type হলো never।



আরেকটি ব্যবহার: Exhaustive Checking



type Shape = "circle" | "square";



function draw(shape: Shape) {

 switch (shape) {

   case "circle":

    return "Circle";



   case "square":

     return "Square";



   default: {

     const impossible: never = shape;

     return impossible;

   }

 }

}

এখানে Shape-এর মধ্যে দুটি Value আছে:

. circle

. square

আমরা switch দিয়ে দুটি Value-ই Handle করেছি।



এখন ভবিষ্যতে যদি Shape-এর মধ্যে নতুন কোনো Value যোগ করি, কিন্তু switch-এ সেটি Handle না করি, তাহলে TypeScript Error দেখাবে।



এভাবে আমরা বুঝতে পারব যে কোনো Case বাদ পড়েছে কি না।



## Conclusion

any ব্যবহার করলে TypeScript-এর Type Checking বন্ধ হয়ে যায়।



unknown ব্যবহার করলে কোনো Value ব্যবহার করার আগে সেটির Type সঠিকভাবে যাচাই করতে হয়।



never এমন একটি Value বোঝায়, যা কখনো ঘটতে পারে না।



যখন কোনো Value-এর Type আগে থেকে জানা থাকে না, তখন any-এর পরিবর্তে unknown ব্যবহার করা ভালো। কারণ unknown ব্যবহারের ক্ষেত্রে Value-এর Type যাচাই না করা পর্যন্ত TypeScript আমাদের নিরাপত্তা বজায় রাখে।



