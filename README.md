# The Coding Interview Guide

> This is a collection of my notes when I was/am studying for interviews (or just for myself) 
> and it is also intended to become a systematic guide for people who would like to 
> become a software development engineer (SDE).

> I was graduated as an Electrical Engineer and after working for about 2 years as Electrical
> Engineer I decided to become a Software Engineer. I have taught myself all the most common
> data structures and algorithms, machine learning fundamentals, and backend architectures.

> During my learning journey, I found that I learned all the knowledge piece by piece 
> when I need them, but I was always lack of a systematic understanding/overview of the 
> algorithms or a tech-stack. And since I made lots of notes, I think its necessary to 
> summarize them and make them a systematic guide for whoever wants to become a software 
> development engineer.

> Hope this repo is helpful and best of luck to you!


## A bit more about myself and this repo

I was graduated from a traditional Electrical Engineering program (Yes I don't have a CS/CE degree)
and after that I finished a graduate degree in nano-photonics. 

The only programming courses I took in school was a C++ introductory course in my first year 
undergrad, and an assembly language course in my third year (EE mandatory). I learnt all the other 
programming languages and more all by myself and I understand how painful or missing direction this
could be. 

In this repo I'm going to show you how to get started for people who want to switch career 
or who want to improve the interviewing technics or revisit the fundamentals.

- I'll be giving resources that I learnt 
- I'll be sharing the tips and tricks on how to practice for the algorithms
- I'll talk about various areas of software development
- I'll be sharing the technics for answering Behavior Questions (BQs)

Most importantly, learning is a life long journey, and I'm still learning everyday.
Hopefully you can learn with me, and I can help people getting into the field more easily
or improving their technical abilities.


## Before get started, REMEMBER the following facts

- **Programming is about writing the code, not reading**. So don't just read, IMPLEMENT it!
- **You can't memorize everything at the first time**. So keep repeating and practicing, and WRITE them down!
- **Don't feel you aren't smart enough**. In fact a lot of programming questions are tricky since you've never seen them before. Once you've seen enough, you'll know the tricks.
- **Review, review, review**. Review your code and your notes once a while, try to refactor/optimize your code, and refresh your memories about the fundamentals.
- **Learning is a life lon journey**. So keep learning and reading!

Above points are really really important, keep these in mind and they'll help you in your career.

Now let's get started!


## Table of Content

- [The Coding Interview Guide](#the-coding-interview-guide)
  - [A bit more about myself and this repo](#a-bit-more-about-myself-and-this-repo)
  - [Before get started, REMEMBER the following facts](#before-get-started-remember-the-following-facts)
  - [Table of Content](#table-of-content)
  - [Question & Answer](#question--answer)
    - [Large Company VS Small Company](#large-company-vs-small-company)
    - [What's the interview process look like](#whats-the-interview-process-look-like)
    - [How to use LeetCode as a beginner](#how-to-use-leetcode-as-a-beginner)
    - [How to solve LeetCode problem EFFECTIVELY](#how-to-solve-leetcode-problem-effectively)
    - [How to solve LeetCode problem EFFICIENTLY](#how-to-solve-leetcode-problem-efficiently)
    - [Pay close attention to these when solving problem (gain max value of leetcode problem)](#pay-close-attention-to-these-when-solving-problem-gain-max-value-of-leetcode-problem)
    - [How to get your FIRST job! (How to become more competitive among the candidates)](#how-to-get-your-first-job-how-to-become-more-competitive-among-the-candidates)
  - [Algorithms and Data Structures](#algorithms-and-data-structures)
    - [Data Structures](#data-structures)
      - [Array](#array)
      - [Linked List](#linked-list)
        - [Search, Sort, Insert, Delete, Revert](#search-sort-insert-delete-revert)
        - [Loop in Linked List](#loop-in-linked-list)
      - [Stack](#stack)
      - [Queue](#queue)
      - [Hash Table](#hash-table)
    - [Search and Sort](#search-and-sort)
      - [Search](#search)
        - [Sequential Search](#sequential-search)
        - [Binary Search](#binary-search)
      - [Sort](#sort)
        - [Bubble Sort](#bubble-sort)
        - [Selection Sort](#selection-sort)
        - [Insertion Sort](#insertion-sort)
        - [Shell Sort](#shell-sort)
        - [Merge Sort](#merge-sort)
        - [Quick Sort](#quick-sort)
        - [Heap Sort](#heap-sort)
    - [Trees](#trees)
      - [Tree Operations](#tree-operations)
        - [Tree Traversal: access the nodes of the tree](#tree-traversal-access-the-nodes-of-the-tree)
        - [Search, Insert, Delete](#search-insert-delete)
      - [Binary Search Tree (BST)](#binary-search-tree-bst)
      - [Heap / Priority Queue / Binary Heap](#heap--priority-queue--binary-heap)
      - [More Trees](#more-trees)
    - [Graph](#graph)
    - [Common Algorithm Types](#common-algorithm-types)
  - [System Design](#system-design)
  - [Machine Learning](#machine-learning)
  - [Resources](#resources)
    - [Learn Python](#learn-python)
    - [How to solve Algorithm Questions](#how-to-solve-algorithm-questions)
    - [OOD (Object Oriented Design)](#ood-object-oriented-design)
      - [SOLID Principals](#solid-principals)
      - [Clean Code - Uncle Bob lessons](#clean-code---uncle-bob-lessons)
      - [Design case study](#design-case-study)
    - [Async in Python](#async-in-python)
    - [System Design](#system-design-1)
    - [Machine Learning](#machine-learning-1)
    - [Reinforcement Learning](#reinforcement-learning)


## Question & Answer

**DISCLAIMER:** These QAs are my personal opinions and experience. They are not guaranteed to be the perfect way/solution to the question, but is something I found really helpful from my own experience.

**NOTE:** You should read these QAs first before jumping into the content and resources, since these answers may save you lots time preparing the interview and potentially help you ace the interview. However feel free to go to whatever section you would like to go.

### Large Company VS Small Company

The large companies such as the "Big Five" (Google, Amazon, Facebook, Apple, Microsoft) or the FAANG (Facebook, Amazon, Apple, Netflix, Google) is very attractive to developers, but there are also many smaller companies and startups which makes the majority of the market. 

The debate of whether working for a large company or a small company is ongoing and probably will never stop, since they can be quite different.

The short conclusion is that:

- Large company is a big platform where you can build your network very effectively and gain an insight of how the large company and complex architecture works, the down side is that there will be micromanagement and office politics (to some degree at least), and you can't learn the full development cycle, plus there will be too many meetings and processes to get things done
- Small company allows you to learn the full development cycle, gain a lot of project experience quickly, and release a complete product from idea to production. You'll be spending the majority of your time coding and reviewing code, instead of endless meetings (exclude the mangers because that's what they do, they have to plan the next steps with other departments). The down side is that your company is not well know so your skills could potentially be questioned, and building connections is a bit more difficult.

I've created a table for you. (It is subjective and depending on different teams, numbers are not accurate but to give you an idea)

|     | Large Company | Small Company |
| :-: | :-----------: | :-----------: |
| Networking | Easy to connect to highly talented people | Have to work on networking |
| Programming (varies with different comp) | ~ 30% a day | ~ 70% a day |
| Meetings | ~ 50% - 70% a day | 10% - 30% a day |
| Feature release process | could have many rounds of review and approval process | normally just peer review |
| tech stack | it depends on different teams | it depends on project and the company culture |
| Interview process | Many rounds, from 5 to 10+ | normally 3-5 rounds, sometimes have a take home project |
| Interview Content | Mostly focus on algorithm/data structure problems | Mostly about hands on experience on the company tech stack |

### What's the interview process look like

The interview process normally follows the following steps, but of course each company is different:

1. You'll get an email asking you to finish an Online Assessment (OA) quiz, normally algorithm questions or simple knowledge test for the company's tech stack
    - Note this is mostly used by large companies (and some mid-size companies). Small companies rarely has it.
2. You got contacted by the company that there will be a screening phone interview
    - This step normally is just talking about yourself and go over your resume/experience, and learn more about the company and position
3. A technical phone interview. 
    - This could be anything, from algorithm questions, to language/framework features.
    - Each company is different.
4. Another round of technical phone interview or take home quiz/project
    - If this is not a take home quiz/project, then its referred as the "On-site" where you spend many hours to finish many rounds of interviews (3-5 rounds depending on the company and experience level)
5. This step varies, could be another technical interview, or company culture interview
    - Again not all company has this step, but if you got one then its mostly just to check the candidate with the company culture, or some high level open technical discussions.
6. Offer!

Above steps is just a summary from my own experience (and from what I learnt from my friends). 

DO ask the interviewer/hr the interview process when you got contacted!

### How to use LeetCode as a beginner

- First of all, if you don't know what LeetCode is, google it and thank me later.

- As a beginner or new to algorithm questions, LeetCode can get overwhelming because there are more than 1500 (at the time of writing) problems!

- If you are new to algorithm and data structure, go the "**Explore**" tab on the top navigation bar, and go to the "**Learn**" row and learn all of them.

- If you already know all the data structures, and would like to practice, do the questions from the tags, and do them from easy to hard
    - Note that most of the companies rarely test hard ones

- If you are really familiar with all the data structures and common algorithms, do the problems randomly, so you can think the best data structure for solving the problems most efficiently

- If you are time sensitive/critical (i.e. you have an interview in the near future or you are actively looking for jobs), do the company based questions

### How to solve LeetCode problem EFFECTIVELY

**Rule of thumb: make every question count!**

What I mean is that you have to really understand the question after you've solved it.

It doesn't really matter if you solved it by yourself or looked at the answers. 

Here are a list of important things you have to always think about when you are working on problems:

- What's the best data structure/s to solve this problem
- What's the time and space complexity (Big O's)
- What's the tradeoff for the current approach (i.e. more space or more time)

After solving the question (again whether you solved it yourself or looked at solution/discussion):

- Is your solution the best way to solve it, if not is there a way to optimize your solution
- If you can't solve it yourself, what was the reason?
    - Have you seen the data structure/algorithm before? 
        - If not you should stop working on more problems and study that immediately
        - If so you should practice more on this type of problems
    - Is there any tricks when solving the problem? 
        - If not just keep practicing
        - If so NOTE it!
    - Did you have no clue when seeing the problem? 
        - Practice more of this type of problems, and summarize the solution for each problem solved

If you strictly do above things when you are working on the problem and after you solved it, its just a matter of time until you are an expert.

### How to solve LeetCode problem EFFICIENTLY

**Rule of thumb: Don't work on a single problem for too long, and don't be afraid to look at the solution!**

I know many people don't wanna look for a solution if they can't solve the problem, but spending too much time (i.e hours) on a single problem isn't efficient at all! After all you only have 24 hours a day.

So here is what you should do:

- If you have no clue at all after reading the question, look at solution directly
    - It may sounds a little cheese but this is the most efficient way cause you'll probably have no clue after 1 hour. Once you have solved enough questions this won't happen
- If you have some clue but not sure how to do it, then spend some time work on it
    - Normally spend like 15 - 30 mins, and if you still can't solve it, look at the solution
- If you have an idea on how to solve it, do it!
    - For this case, spend as much time as you need, even its one hour!
    - The reason for that is you know how to solve it, but you are not really familiar on the approach so you need more practice. By solving it on your own after many try and errors, you should be very familiar with this question and you should be able to solve it very quickly next time

To summarize, there are really just two points:

1. Don't be afraid at looking the solution
2. If you are blocked, see point 1

### Pay close attention to these when solving problem (gain max value of leetcode problem)

**Rule of thumb: Consider edge cases, explain it step by step, analyze complexities, walk through code for test case**

To gain the max value of leetcode problems, you need to do more than just solve the problem. 

Here are a few things you need to pay close attention when solving the problem, because doing so will get you prepared for an interview better:

- When first see the problem, ask many questions like boundaries, some edge case etc.
    - Leetcode problems are quite straightforward, it shows you pretty much everything. However in the interview you'll have to work with the interviewer to get all the details of the problem you are about to solve. Make sure you fully understand the question and is aware of the boundaries and any possible edge cases
- When solving the problem, don't just jump right in writing the code, but try to explain what you are about to do first by writing some pseudo code to illustrate your thinking process. 
    - Doing so will allow your interviewer to understand your approach, and possibly correct you (or guide you) to the right path
    - You can actually follow this process when working on the leetcode problems. For example, you can first write down the pseudo code as comments, and then fill in the actual code
    - Since communication is also a really important factor in the interview process, this explanation step will greatly prepare you for an actual interview
- You can ask for the space and time complexities prior to solving the problem, but most of the time you should mention this after finishing the problem. 
    - Make sure you analyze both time and space complexity
- Last but not least, once you have the solution, make sure to walk through your code with an test case. 
    - Believe it or not, a lot people cannot debug their own code!
    - Doing so will also show a sign that you review your code first before pushing it out, which is something you should do on your daily job 

### How to get your FIRST job! (How to become more competitive among the candidates)

To begin with, this is not limited to how to get the first job, but is meant to show you how to stand out of the crowd.

**Rule of thumb: build your reputation, gain more project experience, networking!!**

Essentially, you'll need to build your reputation. How to do that? There are a few ways:

- **Attending meetups!** First and for most!
    - Meetups, especially local meetups give you the opportunities to directly talk to a person who has a job, and whose company might be hiring. So if you go to meetups frequently and make connections, job opportunities will come to you!

- Make sure you resume and **LinkedIn profile** (especially this one!) is up-to-date!
    - The recruiters and agents are quite active on linkedin, and I received a lot of interests from them.

- Gain more project experience. **Either contribute to open source project or make your own personal project.**
    - This is not only for new grads, but also for those who have a few years of experience but has no project to show.
    - I'm sure you all have lots of project experience from work, but I'm afraid you can't show them to the interviewer! The personal project is a way to SHOW OFF your skills and codes, and a way to convince the HR/interviewer that you are a strong candidate
    - NOTE: most of the time HR/interviewer will not look at your pet project, but you can still let them know and probably brag about it during your interview, it'll always add scores!
    - At last, make sure your pet project has quality code and follow standards! Otherwise it won't help.

- Apply to many jobs and **don't shy to ask for help**.
    - **Don't restrict yourself!** For first job, make sure you are fully prepared and apply to all companies that you can apply to, don't limit yourself to only large companies or certain companies. After all, once you had your first job, it'll be easier to find the second one, third one, etc
    - Ask your network for potential job opportunities. Don't be shy to ask around, but make sure you are polite and not harassing people. It doesn't hurt to ask and sometimes the result may surprise you.

- **Don't give up!** If you can't find a job or even receive any responses, **its not your fault**.
    - Most companies won't response if you are not a good match nowadays. I know it doesn't feel good and you feel like you are just hanging there, but be aware that its not your fault.

A lot times finding jobs is more of luck than anything else, so be prepared, be patient, and don't give up!

Good luck!!!


## Algorithms and Data Structures

**Book:** [Problem Solving with Algorithms and Data Structures using Python](https://runestone.academy/runestone/books/published/pythonds/index.html)

### Data Structures

#### Array

#### Linked List

##### Search, Sort, Insert, Delete, Revert

##### Loop in Linked List

#### Stack
#### Queue
#### Hash Table

### Search and Sort

#### Search

##### Sequential Search
##### Binary Search

- KEY is the search interval
- [Template](./Templates/binary_search.md)

#### Sort

##### Bubble Sort
##### Selection Sort
##### Insertion Sort
##### Shell Sort
##### Merge Sort
##### Quick Sort
##### Heap Sort

### Trees

#### Tree Operations

##### Tree Traversal: access the nodes of the tree

- **preorder:** visit root first, then recursively do traversal of the left subtree,then a recursive traversal of the right subtree.
    - root -> left -> right
- **inorder:** recursively do traversal on the left subtree, then the root node, and finally do traversal of the right subtree.
    - left -> root -> right
- **postorder:** do traversal of the left subtree and the right subtree, finally to the root node.
    - left -> right -> root
- Level-order
- BFS
- DFS

##### Search, Insert, Delete


#### Binary Search Tree (BST)

- BST Property:
    1. The value in each node must be `greater than (or equal to)` any values stored in its left subtree.
    2. The value in each node must be `less than (or equal to)` any values stored in its right subtree.
- `Inorder traversal` in BST will be in `ascending order`. Therefore, the inorder traversal is the most frequent used traversal method of a BST.
- **successor:** the node that has the next-largest key in the tree
    - it has no more than one child

- Balanced BST

#### Heap / Priority Queue / Binary Heap

- **Priority Queue:**
    - the logical order of items inside a queue is determined by their priority.
    - The highest priority items are at the front of the queue and the lowest priority items are at the back.
- **Binary Heap:** the classic way to implement a priority queue.
    - both enqueue and dequeue items are **O(logn)**
    - **min heap:** the smallest key is always at the front
    - **max heap:** the largest key value is always at the front
    - **complete binary tree:** a tree in which each level has all of its nodes (except the bottom level)
        - can be implemented using a single list
        - Because the tree is complete, the left child of a parent (at position **p**) is the node that is found in position **2p** in the list. Similarly, the right child of the parent is at position **2p+1** in the list.
        ![](http://interactivepython.org/runestone/static/pythonds/_images/heapOrder.png)
    - **heap order property:** In a heap, for every node **x** with parent **p**, the key in **p** is smaller than or equal to the key in **x**.
        * For example, the root of the tree must be the smallest item in the tree
    - When to use heap:
        - Priority Queue implementation
        - whenever need quick access to largest/smallest item
            - Instant access to the item
            - insertions are fast, allow in-place sorting
        - More details can be seen in [this discussion](https://stackoverflow.com/questions/749199/when-would-i-want-to-use-a-heap)

#### More Trees

- AVL Tree
- Red-Black Tree
- B+ Tree
- Trie
    - [Template](./Templates/trie.md)


### Graph

- Directed Graph
- Undirected Graph
- Graph Representation
    - Adjacency Matrix
    - Adjacency List
- Graph traversal: BFS & DFS
- Graph Algorithms:
    - Shortest Path:
        - Dijkstra’s Algorithm
        - Floyd Warshall Algorithm
    - Topological Sort
        - [Template](./Templates/topological_sort.md)
    - Prim’s Spanning Tree Algorithm

### Common Algorithm Types

- Backtracking 
- Divide and Conquer
- Dynamic Programming
- Greedy
- Branch and Bound
- Brute Force


## System Design

## Machine Learning

## Resources

### Learn Python

- [Everything About Python — Beginner To Advanced](https://medium.com/fintechexplained/everything-about-python-from-beginner-to-advance-level-227d52ef32d2)

### How to solve Algorithm Questions

- [Fucking Algorithm - Algorithm template - Java, Python - English, Chinese](https://github.com/labuladong/fucking-algorithm)
- [Algorithm Pattern - Algorithm template - Go - Chinese](https://github.com/greyireland/algorithm-pattern)
- [Hello Algorithm - Leetcode Solution - Java - English, Chinese](https://github.com/geekxh/hello-algorithm)
- [LeetCode Topics and Interview Questions Collection - Leetcode Solution - Java - English, Chinese](https://github.com/yuanguangxin/LeetCode)

### OOD (Object Oriented Design)

#### SOLID Principals

- [S.O.L.I.D. Principles of Object-Oriented Design - A Tutorial on Object-Oriented Design](https://www.youtube.com/watch?v=GtZtQ2VFweA&ab_channel=LaraconEU)
- [Understanding the Single Responsibility Principle](https://www.youtube.com/watch?v=L2m-S0Pj_Xk&ab_channel=edutechional)
- [Understanding the Open Closed Principle](https://www.youtube.com/watch?v=Ryhy7333mqQ&ab_channel=edutechional)
- [Understanding the Liskov Substitution Principle](https://www.youtube.com/watch?v=Mmy1EUKC_iE&ab_channel=edutechional)
- [OOP Design Principles: Interface Segregation Principle](https://www.youtube.com/watch?v=Ye1h3zKl1lg&ab_channel=edutechional)
- [OOP Design Principles: Dependency Inversion Principle](https://www.youtube.com/watch?v=qL2-5g_lJTs&ab_channel=edutechional)
- [Refactoring From Trash to SOLID](https://medium.com/swlh/refactoring-from-trash-to-solid-74b10005ccd3)

#### Clean Code - Uncle Bob lessons

Uncle Bob, whose a software engineer and introduced teh S.O.L.I.D. principals for clean code writing. 

Here is a recent series of his open talks and I feel its valuable to spend time watching them at least once.

- [Clean Code - Uncle Bob / Lesson 1: SOLID principals, refactor, DRY](https://www.youtube.com/watch?v=7EmboKQH8lM&ab_channel=UnityCoin)
- [Clean Code - Uncle Bob / Lesson 2: Comments, docs, naming,  reviews](https://www.youtube.com/watch?v=2a_ytyt9sf8&ab_channel=UnityCoin)
- [Clean Code - Uncle Bob / Lesson 3: Software growth, QA, teamwork](https://www.youtube.com/watch?v=Qjywrq2gM8o&ab_channel=UnityCoin)
- [Clean Code - Uncle Bob / Lesson 4: TDD](https://www.youtube.com/watch?v=58jGpV2Cg50&ab_channel=UnityCoin)
- [Clean Code - Uncle Bob / Lesson 5: Architecture, project development](https://www.youtube.com/watch?v=sn0aFEMVTpA&ab_channel=UnityCoin)
- [Clean Code - Uncle Bob / Lesson 6: project management](https://www.youtube.com/watch?v=l-gF0vDhJVI&ab_channel=UnityCoin)

#### Design case study

- **Elevator System Design**:
    - [Video](https://leetcode.com/discuss/interview-question/object-oriented-design/886910/Elevator-System-Design-or-Object-Oriented-System-Design-Interview-Question)
    - [discussion1](https://leetcode.com/discuss/interview-question/object-oriented-design/846057/OODElevator-System-with-N-elevators.)
    - [discussion2](https://leetcode.com/discuss/interview-question/object-oriented-design/124936/design-an-elevator-system)


### Async in Python

- [Demystifying Python's Async and Await Keywords](https://www.youtube.com/watch?v=F19R_M4Nay4&ab_channel=JetBrainsTV)
- [Thinking Outside the GIL with AsyncIO and Multiprocessing - PyCon 2018](https://www.youtube.com/watch?v=0kXaLh8Fz3k&ab_channel=PyCon2018)
- [Advanced asyncio: Solving Real-world Production Problems - PyCon 2019](https://www.youtube.com/watch?v=bckD_GK80oY&ab_channel=PyCon2019)


### System Design

- [Design Patterns](https://www.tutorialspoint.com/design_pattern/filter_pattern.htm)
- [System Design Cheatsheet](https://gist.github.com/vasanthk/485d1c25737e8e72759f)


### Machine Learning

- [100 Days of Machine Learning Coding](https://github.com/Avik-Jain/100-Days-Of-ML-Code)


### Reinforcement Learning

- [Reinforcement Learning Methods and Tutorials](https://github.com/MorvanZhou/Reinforcement-learning-with-tensorflow)
