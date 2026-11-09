TypeScript Access Modifiers



TypeScript-এ Access Modifiers ব্যবহার করা হয় কোনো Class-এর Property (Variable) এবং Method (Function) কোথা থেকে ব্যবহার করা যাবে, তা নিয়ন্ত্রণ করার জন্য।



## Detailed Explanation

. public — সবার জন্য উন্মুক্ত

public মানে হলো কোনো Property বা Method Class-এর বাইরে থেকেও ব্যবহার করা যাবে।



এটি TypeScript-এর Default Modifier। অর্থাৎ কিছু না লিখলেও সেটি public হিসেবে কাজ করে।



class Account {

 public owner: string;



&#x20; constructor(owner: string) {

&#x20;   this.owner = owner;

&#x20; }

}



const account = new Account("Mina");



account.owner = "Rubina";





2\. private — শুধু নিজের Class-এর ভিতরে

private ব্যবহার করলে কোনো Property বা Method শুধু যে Class-এর ভিতরে তৈরি করা হয়েছে, সেখানেই ব্যবহার করা যাবে।



Class-এর বাইরে থেকে সরাসরি Access করা যাবে না।





class Account {

 private balance: number = 500;



 getBalance(): number {

   return this.balance;

 }

}



const account = new Account();



account.getBalance(); // 500



// Error

account.balance;



3\. protected — নিজের Class এবং Child Class-এর জন্য

protected অনেকটা private-এর মতো। তবে এর একটি অতিরিক্ত সুবিধা আছে।



এটি ব্যবহার করা যায়:

\- নিজের Class-এর ভিতরে।

\- Child Class বা Subclass-এর ভিতরে।

কিন্তু Class-এর বাইরে থেকে সরাসরি Access করা যায় না।



class Animal {

 protected name: string;



 constructor(name: string) {

   this.name = name;

 }

}



class Cat extends Animal {

 describe() {

   return `${this.name} is a cat`;

 }

}



const cat = new Cat("Tom");



cat.describe();



// Error

cat.name;



4\. readonly — Value পরিবর্তন করা যাবে না

readonly ব্যবহার করা হয় কোনো Property-এর Value একবার Set করার পর পুনরায় পরিবর্তন করা বন্ধ করতে।



Property-টি Declaration করার সময় অথবা Constructor-এর ভিতরে Value Assign করা যায়।

class Product {

 readonly id: number;



 constructor(id: number) {

   this.id = id;

 }

}



const product = new Product(10);



console.log(product.id); // 10



// Error

product.id = 20;



\## Conclusion



public: Class-এর যেসব Property বা Method বাইরে থেকেও ব্যবহার করা যাবে, সেগুলোর জন্য public ব্যবহার করা হবে।







private: Class-এর অভ্যন্তরীণ কাজের জন্য যেসব Property বা Method শুধু নিজের Class-এর মধ্যে ব্যবহার করা হবে, সেগুলোর জন্য private ব্যবহার করা হবে।







protected: যেসব Property বা Method নিজের Class এবং Child Class-এর মধ্যে ব্যবহার করা যাবে, সেগুলোর জন্য protected ব্যবহার করা হবে।







readonly: যেসব Property-এর Value একবার নির্ধারণ করার পর আর পরিবর্তন করা যাবে না, সেগুলোর জন্য readonly ব্যবহার করা হবে।

