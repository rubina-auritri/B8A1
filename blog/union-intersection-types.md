# TypeScript-এ Union এবং Intersection Types



TypeScript-এ Union (|) এবং Intersection (\&) ব্যবহার করে একাধিক Type একসঙ্গে ব্যবহার করা যায়।

Union (|) এবং Intersection (\&) টাইপ ব্যবহার করে TypeScript-এ একাধিক Data  টাইপকে বিভিন্নভাবে একত্রিত করা যায়।







#### \## Detailed Explanation



১. Union Type (|) – অথবা (OR)



Union Type মানে একটি variable একাধিক Type-এর যেকোনো একটি হতে পারে।





let value: string | number;



value = "Hello";

value = 100;



এখানে value-এর মধ্যে String অথবা Number রাখা যাবে।



আরেকটি বাস্তব উদাহরণ দেখি।



type Success = {

&#x20; status: "success";

&#x20; data: string;

};



type Failure = {

&#x20; status: "error";

&#x20; message: string;

};



type ApiResult = Success | Failure;





এখানে API থেকে দুই ধরনের Result আসতে পারে:

\- Success হলে data থাকবে।

\- Error হলে message থাকবে।



function showResult(result: ApiResult): string {

&#x20; if (result.status === "success") {

&#x20;   return result.data;

&#x20; }



&#x20; return result.message;

}





২. Intersection Type (\&) – এবং (AND)



Intersection Type মানে একাধিক Type-এর সব Property একসঙ্গে থাকতে হবে।

প্রথম Type:

type User = {

&#x20; id: number;

&#x20; name: string;

};



দ্বিতীয় Type:

type Timestamped = {

&#x20; createdAt: Date;

};



এখন আমরা দুটি Type একসঙ্গে করব।

type UserRecord = User \& Timestamped;



এখন একটি Object তৈরি করি:

const record: UserRecord = {

&#x20; id: 1,

&#x20; name: "Nila",

&#x20; createdAt: new Date()

};





৩. Union এবং Intersection একসঙ্গে ব্যবহার





type Profile = {

&#x20; id: number;

&#x20; name: string;

};



type Member = {

&#x20; role: "member";

&#x20; points: number;

};



type Moderator = {

&#x20; role: "moderator";

&#x20; permissions: string\[];

};



type Account = Profile \& (Member | Moderator);



Member Account:

const user1: Account = {

&#x20; id: 1,

&#x20; name: "Nila",

&#x20; role: "member",

&#x20; points: 100

};



Moderator Account:



const user2: Account = {

&#x20; id: 2,

&#x20; name: "Rahim",

&#x20; role: "moderator",

&#x20; permissions: \["edit", "delete"]

};



#### &#x20;## Conclusion

যখন কোনো Object-এর structure বা কী কী property থাকবে, সেটা define করতে চাইবে, বিশেষ করে Public API বানানোর ক্ষেত্রে, তখন interface ব্যবহার করাই ভালো। কারণ পরে Declaration Merging-এর মাধ্যমে interface-এ নতুন property যোগ করা যায়।



অন্যদিকে, Union (|), Intersection (\&), Tuple, Primitive বা একটু জটিল Type তৈরি করতে চাইলে type ব্যবহার করা ভালো।

