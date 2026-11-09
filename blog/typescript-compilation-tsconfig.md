TypeScript Compilation: tsc এবং tsconfig.json কীভাবে কাজ করে





&#x20;Introduction 

Browser এবং Node.js সরাসরি JavaScript কোড চালায়, TypeScript-এর নিজস্ব Syntax সরাসরি চালাতে পারে না।



তাই TypeScript কোডকে JavaScript-এ রূপান্তর করতে TypeScript Compiler ব্যবহার করা হয়। এই Compiler-কে সংক্ষেপে tsc বলা হয়।



অন্যদিকে, tsconfig.json ফাইলের মাধ্যমে TypeScript Compiler-কে বলে দেওয়া হয়, কীভাবে আমাদের Project-এর কোড পরীক্ষা (Type Checking) এবং Compile করতে হবে।



&#x20;Compilation কীভাবে কাজ করে?

যখন আমরা TypeScript কোড Compile করি, তখন কয়েকটি ধাপ সম্পন্ন হয়:

1\. Parsing: Compiler প্রথমে TypeScript কোড পড়ে এবং তার গঠন বোঝে।

2\. Module Resolution: কোন ফাইল থেকে কোন ফাইল Import করা হয়েছে, তা খুঁজে বের করে।

3\. Type Checking: কোডে Type-এর কোনো ভুল আছে কি না, তা পরীক্ষা করে।

4\. JavaScript Output: সবকিছু ঠিক থাকলে TypeScript কোড থেকে JavaScript তৈরি করে।



interface User {

&#x20; name: string;

}



const user: User = {

&#x20; name: "Asha"

};



console.log(user.name);



এখানে User একটি Interface এবং : User একটি Type Annotation।



Compile করার পর JavaScript ফাইলটি এমন হবে:



const user = {

&#x20; name: "Asha"

};



console.log(user.name);





tsconfig.json কী?

tsconfig.json হলো TypeScript Project-এর প্রধান Configuration File।



এই ফাইলের মাধ্যমে Compiler-কে বিভিন্ন নিয়ম নির্ধারণ করে দেওয়া যায়।



যেমন:

\- কোন JavaScript Version তৈরি হবে।

\- কোন Module System ব্যবহার হবে।

\- কতটা Strict Type Checking হবে।

\- TypeScript ফাইল কোথায় থাকবে।

\- তৈরি হওয়া JavaScript ফাইল কোথায় জমা হবে।

প্রথমে Terminal-এ নিচের Command চালিয়ে Configuration File তৈরি করা যায়:



npx tsc --init



sconfig.json-এর গুরুত্বপূর্ণ Options

একটি সহজ Configuration দেখি:

{

&#x20; "compilerOptions": {

&#x20;   "target": "ES2020",

&#x20;   "module": "ESNext",

&#x20;   "strict": true,

&#x20;   "outDir": "./dist",

&#x20;   "rootDir": "./src",

&#x20;   "noEmitOnError": true

&#x20; },

&#x20; "include": \["src"]

}



১. target

&#x20;"target": "ES2020"  এটি নির্ধারণ করে Compile হওয়ার পর JavaScript কোন Version-এর হবে।



যেমন: ES5, ES6, ES2020 ইত্যাদি।



২. module

"module": "ESNext"

এটি নির্ধারণ করে JavaScript-এ কোন Module System ব্যবহার করা হবে।



যেমন: ESNext, CommonJS ইত্যাদি।

৩. strict

এটি চালু করলে TypeScript আরও কঠোরভাবে Type Checking করবে।



ফলে অনেক ধরনের ভুল আগেই ধরা পড়বে।

৪. rootDir

"rootDir": "./src"

এটি নির্ধারণ করে আমাদের মূল TypeScript Source Code কোন Folder-এ থাকবে।



৫. outDir

"outDir": "./dist"

Compile হওয়ার পর তৈরি হওয়া JavaScript ফাইলগুলো কোন Folder-এ জমা হবে, সেটি নির্ধারণ করে।

৬. noEmitOnError

"noEmitOnError": true

এর অর্থ হলো TypeScript-এ Compilation Error থাকলে JavaScript Output তৈরি করা হবে না।



Conclusion 

tsc হলো TypeScript Compiler, যা TypeScript কোড পরীক্ষা করে এবং JavaScript তৈরি করতে পারে। অন্যদিকে, tsconfig.json ফাইলের মাধ্যমে পুরো Project-এর Compilation এবং Type Checking-এর নিয়ম নির্ধারণ করা হয়।





