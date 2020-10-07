# The Coding Interview Guide

> This is a collection of my notes when I was/am studying for interviews and it is also
> intended to become a systematic guide for people who would like to become a software 
> development engineer.

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
or who want to improve on the interviewing technics or revisit the fundamentals.

- I'll be giving resources that I learnt 
- I'll be sharing the tips and tricks on how to practice on the algorithms
- I'll talk about various areas of software development
- I'll be sharing the technics for Behavior Questions (BQs)

Most importantly, learning is a life long journey, and I'm still learning everyday.
Hopefully you can learn with me, and I can help people getting into the field more easily
or improve their technical abilities.


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


## Question & Answer

**DISCLAIMER:** These QAs are my personal opinions and experience. They are not guaranteed to be the perfect way/solution to the question, but is something I found really helpful from my own experience.

### Large Company VS Small Company

The large companies such as the "Big Five" (Google, Amazon, Facebook, Apple, Microsoft) or the FAANG (Facebook, Amazon, Apple, Netflix, Google) is very attractive to developers, but there are also many smaller companies and startups which takes the majority of the market. 

The debate of whether working for a large company or a small company is ongoing and probably will never stop, since there is really a lot differences.

The short conclusion is that:

- Large company is a big platform where you can build your network very effectively and gain an insight of how the large company works, the down side is that there will be micromanagement (to some degree at least) and office politics, and you can't learn the full development cycle, plus there will be many meetings and too many processes
- Small company enables you the ability to learn the full development cycle, gain a lot of project experience, and release a complete product from idea to production. You'll be spending the majority of your time coding and review coding, instead of endless meetings (exclude the mangers coz that's what they do, they have to plan the next steps with other departments). The down side is that your company is not well know so your skills could potentially be questioned, and building connections is a bit more difficult.

I've created a table for you.

|     | Large Company | Small Company |
| :-: | :-----------: | :-----------: |
| Networking | Easy to connect to many famous programmers | Have to work on networking |
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
    - If this is not a take home quiz/project, then its referred as the "On-site" where you spend many hours to finish many rounds of interviews (3-5 depending on the company and experience level)
5. This step varies, could be another technical interview, or company culture interview
    - Again not all company has this step, but if you got one then its mostly just to check the candidate with the company culture, or some high level open technical discussions.
6. Offer!

Above steps is just a summary from my own (and from what I learnt from my friends) experience. 

Do ask the interviewer/hr the interview process when you got contacted!

### How to use LeetCode as a beginner

- First of all, if you don't know what LeetCode is, google it and thank me later.

- As a beginner or new to algorithm questions, LeetCode can get overwhelming coz there are more than 1500 (at the time of writing) problems!

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
