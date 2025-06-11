<details> 
<summary>What is PostgreSQL?</summary>
PostgreSQL  একটি ওপেন-সোর্স, অবজেক্ট-রিলেশনাল ডাটাবেস ম্যানেজমেন্ট সিস্টেম (ORDBMS)। এটি একটি শক্তিশালী, ফিচার-সমৃদ্ধ এবং স্থিতিশীল ডাটাবেস সিস্টেম, যা বড় ধরনের অ্যাপ্লিকেশন এবং ওয়েবসাইটের ব্যাকএন্ডে ব্যবহৃত হয়।

এটি মূলত রিলেশনাল ডাটাবেস এর উপর ভিত্তি করে তৈরি, তবে এতে অবজেক্ট ওরিয়েন্টেড ফিচার ও এক্সটেনশন সাপোর্টও আছে।

**PostgreSQL-এর ইতিহাস:**
 এর যাত্রা শুরু হয় 1986 সালে, University of California, Berkeley-তে। প্রকল্পের নাম ছিল POSTGRES। পরে SQL সাপোর্ট যুক্ত করে নাম রাখা হয় PostgreSQL। এটি এখন PostgreSQL Global Development Group দ্বারা পরিচালিত হয়।

**PostgreSQL-এর বৈশিষ্ট্যসমূহ (Features):**

1. **ওপেন সোর্স ও ফ্রি:**
   PostgreSQL সম্পূর্ণভাবে ফ্রি এবং ওপেন সোর্স; আপনি ইচ্ছামত ব্যবহার, কাস্টমাইজ বা পরিবর্তন করতে পারেন।

2. **ACID কমপ্লায়েন্ট:**
   এটি ACID (Atomicity, Consistency, Isolation, Durability) রুল অনুসরণ করে, যা ডেটার নিরাপত্তা নিশ্চিত করে।

3. **আধুনিক ডেটা টাইপ সাপোর্ট:**
   যেমন – `JSON`, `XML`, `ARRAY`, `UUID`, `HSTORE` ইত্যাদি।

4. **Stored Procedures ও Triggers:**
   ব্যবহারকারীরা ফাংশন তৈরি করে অটোমেটেড কার্যক্রম করতে পারে।

5. **Full-Text Search:**
   টেক্সট বা ডকুমেন্ট সার্চিং সুবিধা।

6. **Extensibility:**
   ইউজাররা নিজেরা নতুন ফাংশন, অপারেটর বা ডেটা টাইপ যোগ করতে পারে।

7. **MVCC (Multi-Version Concurrency Control):**
   একাধিক ইউজার একসাথে ডেটার সাথে কাজ করলেও কনফ্লিক্ট হয় না।

8. **Replication ও Backup সুবিধা:**
   ডেটার ব্যাকআপ, রিস্টোর এবং রেপ্লিকেশন খুব সহজে করা যায়।

9. **High Performance:**
   PostgreSQL বড় ডেটা ও ট্রানজ্যাকশন হ্যান্ডেল করতে সক্ষম।

</details>



<details>
<summary>What is the purpose of a database schema in PostgreSQL?</summary>

Schema হলো PostgreSQL ডেটাবেসের ভিতরে একটি লজিক্যাল কাঠামো বা namespace, যা বিভিন্ন ডেটাবেস অবজেক্ট যেমন – টেবিল, ভিউ, ফাংশন, ইনডেক্স, সিকোয়েন্স ইত্যাদি সংগঠিতভাবে সংরক্ষণ করে।

**Schema ব্যবহারের মূল উদ্দেশ্যসমূহঃ**

1. **ডেটা অবজেক্ট গুছিয়ে রাখা :**
   স্কিমার মাধ্যমে সংশ্লিষ্ট টেবিল ও অন্যান্য অবজেক্টগুলো একটি নির্দিষ্ট টেবিল রাখা যায়। যেমন, `user` সম্পর্কিত সব টেবিল `user_schema`-তে রাখা যেতে পারে এবং `admin` সম্পর্কিত সব টেবিল `admin_schema`-তে।

2. **Name Conflicts এড়ানো :**
   একই নামের একাধিক টেবিল স্কিমা ব্যবহারের মাধ্যমে রাখা যায়। যেমনঃ

   * `public.users`
   * `admin.users`
     এখানে `users` নাম দুইবার ব্যবহার হলেও স্কিমা আলাদা হওয়ায় কোনো সমস্যা হবে না।

3. **নিরাপত্তা ও এক্সেস কন্ট্রোল:**
   প্রতিটি স্কিমার উপর নির্দিষ্ট ইউজার বা রোলের জন্য পারমিশন সেট করা যায়। এতে করে কোন ইউজার কি দেখতে বা পরিবর্তন করতে পারবে তা নিয়ন্ত্রণ করা সম্ভব হয়।

4. **বড় ডেটাবেসে Management সহজ হয়:**
   একটি বড় অ্যাপ্লিকেশন যেখানে অনেক টেবিল থাকে, সেখানে স্কিমা ব্যবহারে সব কিছু ভাগ করে রাখা যায়। এতে ডেটাবেস পরিচালনা সহজ হয়।

5. **মডিউলার ডিজাইন :**
    বিভিন্ন মডিউল বা ফিচার অনুযায়ী আলাদা স্কিমা ব্যবহার করতে পারেন, যা কোড এবং ডেটা ম্যানেজমেন্টকে আরও সহজ করে।


### **উদাহরণ:**

```sql
CREATE SCHEMA employee_data;

CREATE TABLE employee_data.employees (
  id SERIAL PRIMARY KEY,
  name TEXT,
  salary NUMERIC
);
```

এখানে `employee_data` নামে একটি স্কিমা তৈরি করা হয়েছে, যার ভিতরে `employees` নামের একটি টেবিল রাখা হয়েছে।



PostgreSQL-এ স্কিমা ব্যবহার করলে ডেটাবেস আরও সংগঠিত, নিরাপদ, এবং পরিচালনায় সহজ হয়। এটি বড় প্রজেক্টের জন্য বিশেষভাবে গুরুত্বপূর্ণ।
</details>


<details>
<summary>Explain the Primary Key and Foreign Key concepts in PostgreSQL.</summary>

**Primary Key** হলো একটি কলাম (বা একাধিক কলামের সমন্বয়), যা টেবিলের প্রতিটি রেকর্ডকে অন্য রেকর্ড থেকে আলাদা (unique) করে। 

###  বৈশিষ্ট্য:

* প্রতিটি টেবিলে শুধুমাত্র একটি Primary Key থাকতে পারে।
* এটি স্বয়ংক্রিয়ভাবে unique constraint এবং not null constraint আরোপ করে।

###  উদাহরণ:

```sql
CREATE TABLE students (
  student_id SERIAL PRIMARY KEY,
  name TEXT,
  email TEXT
);
```

এখানে `student_id` হলো Primary Key। এটি প্রতিটি ছাত্রকে ইউনিকভাবে শনাক্ত করবে।

---

## **Foreign Key  কী?**

Foreign Key হলো এমন একটি কলাম, যা অন্য টেবিলের Primary Key-কে রেফারেন্স করে। এটি দুইটি টেবিলের মধ্যে relationship তৈরি করে।

### বৈশিষ্ট্য:

* এটি ডেটাবেসে রেফারেনশিয়াল ইন্টেগ্রিটি নিশ্চিত করে। অর্থাৎ, রেফারেন্স করা মানটি অবশ্যই মূল টেবিলে থাকতে হবে।
* Parent table-এর Primary Key-এর মান না থাকলে child table-এ সেটি ব্যবহার করা যাবে না।

### উদাহরণ:

```sql
CREATE TABLE classes (
  class_id SERIAL PRIMARY KEY,
  class_name TEXT
);

CREATE TABLE students (
  student_id SERIAL PRIMARY KEY,
  name TEXT,
  class_id INT,
  FOREIGN KEY (class_id) REFERENCES classes(class_id)
);
```

এখানে `students` টেবিলের `class_id` একটি Foreign Key, যা `classes` টেবিলের `class_id` কে রেফারেন্স করছে।


##  Tabular পার্থক্য:

| বিষয়                | Primary Key                           | Foreign Key                       |
| ------------------- | ------------------------------------- | --------------------------------- |
| উদ্দেশ্য            | প্রতিটি রেকর্ডকে ইউনিকভাবে শনাক্ত করা | টেবিলগুলোর মধ্যে সম্পর্ক তৈরি করা |
| ইউনিক?              | হ্যাঁ, অবশ্যই ইউনিক                   | না, এটি ডুপ্লিকেট হতে পারে        |
| NULL মান গ্রহণ করে? | না                                    | হ্যাঁ, করতে পারে                  |
| টেবিলের সংখ্যা      | একটি টেবিলে ১টি মাত্র Primary Key     | একাধিক Foreign Key থাকতে পারে     |




* **Primary Key** একটি টেবিলের প্রতিটি রেকর্ডকে অন্য রেকর্ড থেকে আলাদা (unique) করে। 
* **Foreign Key** দুইটি টেবিলের মধ্যে সম্পর্ক স্থাপন করে এবং ডেটার সঠিকতা নিশ্চিত করে।


</details>
<details>
<summary>What is PostgreSQL?</summary>
</details>
<details>
<summary>What is PostgreSQL?</summary>
</details>