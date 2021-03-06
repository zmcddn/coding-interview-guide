# The Coding Interview Guide

> This is a collection of my notes when I was/am studying for interviews (or just for learning) 
> and it is also intended to become a systematic guide for people who would like to 
> become a software development engineer (SDE).

> I was graduated as an Electrical Engineer and after worked 1.5 years as an Electrical
> Engineer I decided to switch to the programming world. I only had one programming course 
> at university and I have taught myself all the most common data structures and
> algorithms, machine learning fundamentals, and software architectures. I started working 
> on leetcode problems at end of Feb 2020, and since then I solve at least 1 problem 
> everyday.

> During my learning journey, I found that I learned all the knowledge piece by piece 
> when I need them, but I was always lack of a systematic understanding/overview. Since 
> I made lots of notes during study, I think its necessary to summarize them and make 
> them a systematic guide for whoever wants to become a software development engineer.

> Hope this repo is helpful and best of luck to you!


## How to use this repo

In this repo I'm going to show you how to get started for those who want to switch career, 
to improve the interviewing technics, or to revisit the fundamentals.

- I'll build a systematic path for data structures, algorithms, and system design problems
- I'll be giving resources that I learnt 
- I'll be sharing the tips and tricks on how to practice for the algorithms
- I'll talk about various areas of software development
- I'll be sharing the technics for answering Behavior Questions (BQs)

Most importantly, learning is a life long journey, and I'm still learning everyday.
Hopefully you can learn with me, and I can help people getting into the field more easily
or improving their technical abilities.

***How to use this repo:***
![how to use this repo](./images/how-to-use-the-repo.png)

Basically, you should use this repo as a guide (yeah the name kinda indicates) to build your own knowledge base and templates.

And if you have enough time, you should go over every topics. If not you can just read the topics you are interested.


## Before get started, REMEMBER the following facts

- **Programming is about writing the code, not reading**. So don't just read, IMPLEMENT it!
- **You can't memorize everything at the first time**. So keep repeating and practicing, and WRITE them down!
- **Don't feel you aren't smart enough**. In fact a lot of programming questions are tricky since you've never seen them before. Once you've seen enough, you'll know the tricks.
- **Review, review, review**. Review your code and your notes once a while, try to refactor/optimize your code, and refresh your memories about the fundamentals.
- **Learning is a life lon journey**. So keep learning and reading!

Above points are really really important, keep these in mind and they'll help you in your career.

Now let's begin our journey!


## Table of Content

- [The Coding Interview Guide](#the-coding-interview-guide)
  - [How to use this repo](#how-to-use-this-repo)
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
  - [Data Structures and Algorithms](#data-structures-and-algorithms)
    - [Data Structures](#data-structures)
      - [Array](#array)
      - [Linked List](#linked-list)
      - [Stack](#stack)
      - [Queue](#queue)
      - [Hash Table](#hash-table)
      - [Trees](#trees)
        - [Tree Traversal: access the nodes of the tree](#tree-traversal-access-the-nodes-of-the-tree)
        - [Binary Search Tree (BST)](#binary-search-tree-bst)
        - [Heap / Priority Queue / Binary Heap](#heap--priority-queue--binary-heap)
        - [More Trees](#more-trees)
      - [Graph](#graph)
    - [Common Algorithm Types](#common-algorithm-types)
      - [Brute Force](#brute-force)
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
      - [Recursion](#recursion)
        - [Recursive function in Python](#recursive-function-in-python)
      - [Backtracking](#backtracking)
      - [Dynamic Programming](#dynamic-programming)
      - [Divide and Conquer](#divide-and-conquer)
      - [Greedy](#greedy)
      - [Branch and Bound](#branch-and-bound)
    - [Frequently Used Technics and Algorithms](#frequently-used-technics-and-algorithms)
    - [Summary](#summary)
  - [System Design](#system-design)
    - [System Design Interview Template](#system-design-interview-template)
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


## Data Structures and Algorithms

**Book:** [Problem Solving with Algorithms and Data Structures using Python](https://runestone.academy/runestone/books/published/pythonds/index.html)

- For those who needs to study the fundamental data structures and algorithms, highly recommend to go over above textbook thoroughly first, and then come back to the following content, or practice on Leetcode or other platform


**Basic data structures**:

- Array
- Linked List
- Stack
- Queue
- Hash Table
- Tree
- Graph

**Common Algorithm Types**:

- Brute Force
- Search and Sort
- Recursive
- Backtracking 
- Dynamic Programming
- Divide and Conquer
- Greedy
- Branch and Bound

**Big O Notations**:

- It is critical that you understand and are able to calculate the Big O for the code you wrote.
- **The order of magnitude function describes the part of T(n) that increases the fastest as the value of n increases. Order of magnitude is often called Big-O notation (for “order”) and written as O(f(n)).**  

- Basically, the Big O measures the number of assignment statements

    | f(n)    | Name        |
    | :-----  | :----       |
    | 1       | Constant    |
    | log n   | Logarithmic |
    | n       | Linear      |
    | n log n | Log Linear  |
    | n^2     | Quadratic   |
    | n^3     | Cubic       |
    | 2^n     | Exponential |

    ![BigO Image](https://runestone.academy/runestone/books/published/pythonds/_images/newplot.png)


### Data Structures

#### Array

- An array (in Python its called *list*) is a collection of items where each item holds a relative position with respect to the others.

#### Linked List

- Similar to array, but requires O(N) time on average to visit an element by index
- Linked list utilize memory better than array, since it can use discrete memory space, whereas array must use continuous memory space
- [Details and Templates](./Templates/linked_list.md)

#### Stack

- Stacks are fundamentally important, as they can be used to reverse the order of items. 
- The order of insertion is the reverse of the order of removal.
- Stack maintain a FILO (first in last out) ordering property.
- When pop is called on the end of the list it takes O(1) but when pop is called on the first element in the list or anywhere in the middle it is O(n) (in Python).

#### Queue

- A queue is structured as an ordered collection of items which are added at one end, called the “rear,” and removed from the other end, called the “front.” 
- Queues maintain a FIFO ordering property.
- A ***deque***, also known as a double-ended queue, is an ordered collection of items similar to the queue. 
    - It has two ends, a front and a rear, and the items remain positioned in the collection. 
    - New items can be added at either the front or the rear. 
    - Likewise, existing items can be removed from either end.

#### Hash Table

- A **hash table** is a collection of items which are stored in such a way as to make it easy to find them later. 
- Each position of the hash table, often called a slot, can hold an item and is named by an integer value starting at 0.
- The mapping between an item and the slot where that item belongs in the hash table is called the **hash function**.
	- **Remainder method** takes an item and divides it by the table size, returning the remainder as its hash value (i.e. `h(item) = item % 11`)
	- **load factor** is the number of items devided by the table size
	- **collision** refers to the situation that multiple items have the same hash value
	- **folding method** for constructing hash functions begins by dividing the item into equal-size pieces (the last piece may not be of equal size). These pieces are then added together to give the resulting hash value. 
	- **mid-square method** first squares the item, and then extract some portion of the resulting digits. For example, 44^2 = 1936, extract middle two digits 93, then perform remainder step (93%11=5).
- **Collision Resolution** is the process to systemacticly place the second item in the hash table when two items hash to the same slot.
- **Open addressing (linear probing):** sequentially find the next open slot or address in the hash table 
	- A disadvantage to linear probing is the tendency for clustering; items become clustered in the table.
	- **Rehashing** is one way to deal with clustering, which is to skip the slot when looking  sequentially for the next open slot, thereby more evenly distributing the items that have caused collisions.
- **Quadratic probing:** instead of using a constant “skip” value, we use a rehash function that increments the hash value by 1, 3, 5, 7, 9, and so on. This means that if the first hash value is h, the successive values are h+1, h+4, h+9, h+16, and so on.
- **Chaining** allows many items to exist at the same location in the hash table. 
	- When collisions happen, the item is still placed in the proper slot of the hash table. 
	- As more and more items hash to the same location, the difficulty of searching for the item in the collection increases.    
	![](http://interactivepython.org/runestone/static/pythonds/_images/chaining.png)
- The initial size for the hash table has to be a prime number so that the collision resolution algorithm can be as efficient as possible.

#### Trees

* A tree data structure has its root at the top and its leaves on the bottom.
* Three properties of tree:
    1. we start at the top of the tree and follow a path made of circles and arrows all the way to the bottom.
    2. all of the children of one node are independent of the children of another node.
    3. each leaf node is unique. 
* **binary tree:** each node in the tree has a maximum of two children.
    * A **balanced binary tree** has roughly the same number of nodes in the left and right subtrees of the root.

##### Tree Traversal: access the nodes of the tree

- Tree traversal is the foundation of all tree related problems.
- Here are a few different ways to traverse a tree:
    - BFS: Level-order
    - DFS: Pre-order, In-order, Post-order
    - [Details and Templates](./Templates/tree_traversal.md)


##### Binary Search Tree (BST)

- BST Property (left subtree < root < right subtree):
    1. The value in each node must be `greater than (or equal to)` any values stored in its left subtree.
    2. The value in each node must be `less than (or equal to)` any values stored in its right subtree.
- `Inorder traversal` in BST will be in `ascending order`. Therefore, the inorder traversal is the most frequent used traversal method of a BST.
- **successor:** the node that has the next-largest key in the tree
    - it has no more than one child
- You could go over the [Leetcode Binary Search Tree topic](https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/) for details

##### Heap / Priority Queue / Binary Heap

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

##### More Trees

- ***Parse tree*** can be used to represent real-world constructions like sentences or mathematical expressions.
    - A simple solution to keeping track of parents as we traverse the tree is to use a stack. 
    - When we want to descend to a child of the current node, we first push the current node on the stack. 
    - When we want to return to the parent of the current node, we pop the parent off the stack.
- ***AVL Tree***: a balanced binary tree. the AVL is named for its inventors G.M. Adelson-Velskii and E.M. Landis.
    - For each node: *balanceFactor* = *height(leftSubTree)* − *height(rightSubTree)*
    - a subtree is left-heavy if *balance_factor > 0*
    - a subtree is right-heavy if *balance_factor < 0*
    - a subtree is perfectly in balance if *balance_factor = 0*
    - For simplicity we can define a tree to be in balance if the balance factor is -1, 0, or 1. 
    - The number of nodes follows the pattern of *Fibonacci sequence*, as the number of elements get larger the ratio of Fi/Fi-1 closes to the golden ratio, so the time complexity is derived to be **O(log n)**
- ***Red-Black Tree***
    - [Details in Wiki](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree)
- ***B+ Tree***: N-array tree
    - [Details in Wiki](https://en.wikipedia.org/wiki/B%2B_tree)
- ***Trie***
    - *This is a common data structure in interviews*
    - [Template](./Templates/trie.md)


#### Graph

- Directed Graph
- Undirected Graph
- Graph Representation
    - Adjacency Matrix (2D matrix)
        - Good when number of edges is large
        - Each of the rows and columns represent a vertex in the graph. 
    - Adjacency List
        - space-efficient way for implementation
        - Each vertix is an element of the list with the vertix as ID and a list of its adjacent vertices as value
- Graph traversal: BFS & DFS
    - [Template](./Templates/graph_traversal.md)
- Graph Algorithms:
    - Shortest Path:
        - Dijkstra’s Algorithm (Single source point)
            - ***Essentially, this is a BFS using priority queue instead of queue***
            - [Template](./Templates/dijkstra.md)
        - Floyd Warshall Algorithm (Multiple source point)
    - Topological Sort
        - [Template](./Templates/topological_sort.md)
    - Prim’s Spanning Tree Algorithm

### Common Algorithm Types

#### Brute Force

- Most common algorithm
- Whenever you are facing a problem without many clues, you should solve it using brute force first, and observe the process and try to optimize your solution 

#### Search

##### Sequential Search

- Sequential Search: visit the stored value in a sequence (use loop)

##### Binary Search

- Examine the middle item of an ordered list
- KEY is the search interval
- [Template](./Templates/binary_search.md)

#### Sort

##### Bubble Sort

- Compares adjacent items and exchanges those that are out of order.
- **Short bubble:** stop early if it finds that the list has become sorted.
- time complexity: O(n2)

##### Selection Sort

- Looks for the largest value as it makes a pass and, after completing the pass, places it in the proper location.
- time complexity: O(n2)

##### Insertion Sort

- Maintains a sorted sub-list in the lower positions of the list. 
- Each new item is then “inserted” back into the previous sub-list such that the sorted sub-list is one item larger.
- time complexity: O(n2)

##### Shell Sort

- Breaks the original list into a number of smaller sub-lists, each of which is sorted using an insertion sort. 
	- the shell sort uses an increment *i*, sometimes called the **gap**, to create a sub-list by choosing all items that are *i* items apart.
	- After all the sub-lists are sorted, it finally does a standard insertion sort
	- time complexity goes between O(n) and O(n2), by changing the increment, a shell sort can perform at O(n^(3/2)).

##### Merge Sort

- A recursive algorithm that continually splits a list in half. 
- [Details and Templates](./Templates/merge_sort.md)

##### Quick Sort

- First selects a value (**pivot value**), and then use this value to assist with splitting the list. 
- [Details and Templates](./Templates/quick_sort.md)

##### Heap Sort

- Use the property of heap to sort the list

#### Recursion

**Recursion** is a method of solving problems that involves breaking a problem down into smaller and smaller sub-problems until you get to a small enough problem that it can be solved trivially. Usually recursion involves a function calling itself.

Three Laws of Recursion:

1. A recursive algorithm must have a base case.
2. A recursive algorithm must change its state and move toward the base case.
3. A recursive algorithm must call itself, recursively.

##### Recursive function in Python

* When a function is called in Python, a stack frame is allocated to handle the local variables of the function. 
* When the function returns, the return value is left on top of the stack for the calling function to access. 
* Even though we are calling the same function over and over, each call creates a new scope for the variables that are local to the function.

#### Backtracking 

- a general algorithm for finding all (or some) solutions to constraint satisfaction problems (i.e. chess, puzzles, crosswords, verbal arithmetic, Sudoku, etc)
- [Template](./Templates/backtrack.md)


#### Dynamic Programming

**Dynamic Programming (DP)** is an algorithm technique which is usually based on a recurrent formula and one (or some) starting states.
	- A sub-solution of the problem is constructed from previously found ones.
	- Usually used to find the extreme cases such as shortest path, best fit, smallest set, etc.

#### Divide and Conquer

- **Divide**: break into non-overlapping sub-problems of the same type (of problem)
- **Conquer**: solve sub-problems
- the algorithm is to keep dividing and conquering, and finally combine them to get the solution
- the algorithm can be written in recursive or loop 

#### Greedy

**Greedy algorithm:**

- find a safe move first
- prove safety
- solve subproblem (which should be similar to original problem)
- estimate running time

**Optimization:**

- assume everything is sorted (if not, maybe sort first)
- decide sort order
- the final running time can be O(n log n) (i.e. sort is O(log n), greedy move can be O(n))

- [More details](https://www.hackerearth.com/practice/algorithms/greedy/basics-of-greedy-algorithms/tutorial/)

#### Branch and Bound

### Frequently Used Technics and Algorithms

**Must know for interview:**

- Matrix Traversal
    - Focusing on various ways of traversing 2D matrix
    - [Template](./Templates/matrix_traversal.md)
- Sliding Window
    - ***Fundamentally this is a two pointer approach***
    - [Template](./Templates/sliding_window.md)
- Union find
    - Essentially its a list representation for the joint data points
    - [Template](./Templates/union_find.md)
- Bit Manipulation
- Prefix Sum
- monotonic stack/queue
    - [Monotonic Stack template](./Templates/monotonic_stack.md)

**Good to know but can be skipped:**

- Segment Tree
- Kadane's algorithm
- Reservoir Sampling
- Line sweep
- KMP algorithm (pattern match)
- Manacher (Longest Palindromic Substring)
- Skip List

### Summary


## System Design

### System Design Interview Template

System design questions can be very difficult to prepare, because it covers a  wide range of areas.

Here is a template I use for the system design interview:

1. Feature expectations (5 mins) - gather requirements:

   - Functional requirements:
       - Use cases
       - Scenarios that will NOT be covered
       - End-user (who will use it)
       - Capacity (how many people will use it, DAU (daily active user))
       - How to use it
   - None-Functional requirements:
       - Scalability
       - Availability
       - Performance/Latency
       - Consistency
       - Durability/Fault-tolerant

2. Estimations (2-5 mins) - estimate scale:

   - Throughput (QPS for read and write queries)
   - Latency expected from the system (for read and write queries)
   - Read/Write ratio (heavy read, heavy write, or similar)
   - Traffic estimates (QPS for read and write)
   - Storage estimates (media files, text/photo/video)
   - Memory estimates
       - Cache: what is the kind of data we want to store in cache
       - How much RAM and how many machines
       - How much data stored on disk/ssd

3. High Level Design (5-10 min) - discuss a very high level with the interviewer:

    - System components (load balancer, services, cache, database, etc)
    - Database schema
    - APIs for Read/Write scenarios for crucial components
    - Request flow process (from client to database)

4. Deep Dive (15-20 mins) - focus on any part of the component:

    - Scaling individual component
        - Availability, Consistency and Scale story for each component
        - Consistency and availability patterns
    - Deep dive on any of the following component
        - DNS
        - CDN (Pull vs Push vs Hybrid)
        - Load Balancer (Round Robin, Weighted Round Robin, Consistent Hash, Active-Passive, Active-Active, Layer 4, Layer 7)
        - Reverse Proxy
        - Application layer scaling (Microservices, Service Discovery, Service Mesh)
        - Database (RDBMS vs NoSQL)
            - RDBMS:
                - Leader-follower, Multi-leader, Leaderless, Federation, Sharding, Denormalization, SQL Tuning
            - NoSQL:
                - Key-Value, Wide-Column, Graph, Document
                - RAM [Bounded size] => Redis, Memcached
                - AP [Unbounded size] => Cassandra, RIAK, Voldemort
                - CP [Unbounded size] => HBase, MongoDB, Couchbase, DynamoDB
        - Caches:
            - Client caching, CDN caching, Webserver caching, Database caching, Application caching, Cache at Query level, Cache at Object level
            - Cache Patterns:
                - Cache aside
                - Write through
                - Write behind
                - Refresh ahead
            - Eviction policies:
                - LRU
                - LFU
                - FIFO
        - Asynchronism
            - Message queues
            - Task queues
            - Back pressure
        - Communication
            - TCP
            - UDP
            - REST
            - RPC

5. Justify (5 mins):

    - Throughput of each layer
    - Latency caused between each layer
    - Overall latency justification


Reference:

- [System Design Template](https://leetcode.com/discuss/career/229177/My-System-Design-Template)
- [System Design - InterviewBit](https://www.interviewbit.com/courses/system-design/)


## Machine Learning

## Resources

### Learn Python

- [Everything About Python — Beginner To Advanced](https://medium.com/fintechexplained/everything-about-python-from-beginner-to-advance-level-227d52ef32d2)

### How to solve Algorithm Questions

- [Fucking Algorithm - Algorithm template - Java, Python - English, Chinese](https://github.com/labuladong/fucking-algorithm)
- [Algorithm Pattern - Algorithm template - Go - Chinese](https://github.com/greyireland/algorithm-pattern)
- [Hello Algorithm - Leetcode Solution - Java - English, Chinese](https://github.com/geekxh/hello-algorithm)
- [LeetCode Topics and Interview Questions Collection - Leetcode Solution - Java - English, Chinese](https://github.com/yuanguangxin/LeetCode)
- [Top 10 algorithms in Interview Questions](https://www.geeksforgeeks.org/top-10-algorithms-in-interview-questions/#algo3)

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

- [The System Design Primer](https://github.com/donnemartin/system-design-primer)
    - The repo with explanations, examples, and study cases
- [Distributed systems for fun and profit](http://book.mixu.net/distsys/single-page.html)
    - About 100 pages free book
- [System Design Cheatsheet](https://gist.github.com/vasanthk/485d1c25737e8e72759f)
    - Quick grasp of system design concepts
- [Design Patterns](https://www.tutorialspoint.com/design_pattern/filter_pattern.htm)
    - You all need to learn the design patterns eventually
- [Design Patterns in Python](https://github.com/faif/python-patterns)

This repo has the full list of company engineering blogs:

- [Engineering Blogs](https://github.com/kilimchoi/engineering-blogs)

Papers:

- [Google MapReduce: Simplified Data Processing on Large Clusters](https://static.googleusercontent.com/media/research.google.com/en//archive/mapreduce-osdi04.pdf)
- [The Google File System](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf)
- [TAO: Facebook’s Distributed Data Store for the Social Graph](https://www.usenix.org/system/files/conference/atc13/atc13-bronson.pdf)
- [Dynamo: Amazon’s Highly Available Key-value Store](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)

### Machine Learning

- [100 Days of Machine Learning Coding](https://github.com/Avik-Jain/100-Days-Of-ML-Code)


### Reinforcement Learning

- [Reinforcement Learning Methods and Tutorials](https://github.com/MorvanZhou/Reinforcement-learning-with-tensorflow)
