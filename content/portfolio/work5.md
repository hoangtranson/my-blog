+++
showonlyimage = false
draft = false
image = "img/portfolio/content5/js1.jpeg"
date = "2018-04-1T23:00:00+07:00"
title = "Clean Code Javascript"
weight = 2
+++

Software engineering principles, from Robert C. Martin's book Clean Code.
<!--more-->

### Table of content
- [Introduction](#introduction)
- [Summary and Integrate to PR](#summary)
- [Variables](#variables)

#### Introduction <a name="introduction"></a>

Software engineering principles, from Robert C. Martin's book Clean Code, adapted for JavaScript. This is not a style guide. It's a guide to producing readable, reusable, and refactorable software in JavaScript.

Not every principle herein has to be strictly followed, and even fewer will be universally agreed upon. These are guidelines and nothing more, but they are ones codified over many years of collective experience by the authors of Clean Code.

Our craft of software engineering is just a bit over 50 years old, and we are still learning a lot. When software architecture is as old as architecture itself, maybe then we will have harder rules to follow. For now, let these guidelines serve as a touchstone by which to assess the quality of the JavaScript code that you and your team produce.

One more thing: knowing these won't immediately make you a better software developer, and working with them for many years doesn't mean you won't make mistakes. Every piece of code starts as a first draft, like wet clay getting shaped into its final form. Finally, we chisel away the imperfections when we review it with our peers. Don't beat yourself up for first drafts that need improvement. Beat up the code instead!

#### Summary and Integrate to PR <a name="summary"></a>

Here is todo list that I created by myself

```
Variables
- [ ] Use meaningful and pronounceable variable names
- [ ] Use the same vocabulary for the same type of variable
- [ ] Use searchable names
- [ ] Use explanatory variables
- [ ] Avoid Mental Mapping
- [ ] Don't add unneeded context
- [ ] Use default arguments instead of short circuiting or conditionals

Functions
- [ ] Function arguments (2 or fewer ideally)
- [ ] Functions should do one thing
- [ ] Functions should only be one level of abstraction
- [ ] Remove duplicate code
- [ ] Set default objects with Object.assign
- [ ] Don't use flags as function parameters
- [ ] Don't write to global functions
- [ ] Favor functional programming over imperative programming
- [ ] Encapsulate conditionals
- [ ] Avoid negative conditionals
- [ ] Avoid conditionals
- [ ] Avoid type-checking
- [ ] Don't over-optimize
- [ ] Remove dead code

Objects and Data Structures
- [ ] Use getters and setters
- [ ] Make objects have private members

Classes
- [ ] Prefer ES2015/ES6 classes over ES5 plain functions
- [ ] Use method chaining
- [ ] Prefer composition over inheritance

SOLID
- [ ] Single Responsibility Principle (SRP)
- [ ] Open/Closed Principle (OCP)
- [ ] Liskov Substitution Principle (LSP)
- [ ] Interface Segregation Principle (ISP)
- [ ] Dependency Inversion Principle (DIP)

Testing
- [ ] Single concept per test

Concurrency
- [ ] Use Promises, not callbacks
- [ ] Async/Await are even cleaner than Promises

Error Handling
- [ ] Don't ignore caught errors
- [ ] Don't ignore rejected promises

Formatting
- [ ] Use consistent capitalization
- [ ] Function callers and callees should be close

Comments
- [ ] Only comment things that have business logic complexity.
- [ ] Don't leave commented out code in your codebase
- [ ] Don't have journal comments
- [ ] Avoid positional markers
```