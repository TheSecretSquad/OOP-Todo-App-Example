# OOP-Todo-App-Example
A Todo App of Exemplary OOP

Authors: James Ladd (@jamesladd) and Peter DiSalvo (@thesecretsquad)

# Purpose
This project documents the process of building a simple (but not too simple) application using exemplary object-oriented design. Exemplary, meaning a developer should be able to read the Domain/Business Logic and almost reconstruct the User Story/Requirement from it.

This project is less about *what* we are building and more about *how* we build it. We intend to reveal the thought process behind testing and designing an object model, as well as other decisions made during development. We are using a Todo application because the domain is simple and recognizable, and lets us freely experiment with general questions about how to test, create a domain-rich object model, and cleanly integrate it with delivery mechanisms (user interfaces, storage mechanisms, etc.)

# Starter Story
> Talking to your users in order to flush out a story is not a simple matter of gathering requirements. What you are actually doing is building a shared understanding of the problem that you’re trying to solve. You are collaborating in order to jointly decide on the best solution. [Alan Holub](https://twitter.com/allenholub/status/1171559931272515584)

The following is our first conversation in developing a user story. In our case, we are playing the roles of Developer and User.

We use the term User and in the ideal situation this is the end User with the problem. Sadly, in most Businesses today this is not this User but a representative of the User such as a Product Manager or Business Analyst.
Try to talk to the end User whenever possible. 

***Initial Story***
```
As a person with things to be done
I want to manage those things
so they get done
```


The single **most important step** a developer can do is to full understand the requirements. We use the term requirements not interchangeable with the term problem. Ideally you are given a problem but this rarely happens so you need to dig deeper to fully understand the problem.
>When do you know the requirements are ambiguous? When they contain words - James Ladd. 

## Questioning the Story and Playing the "5 whys" Game
Here, we ask questions about the story to explore and extract important meaning from the story. Questions include "what" something means or playing the "5 whys" game, where we iteratively ask the question "why?"

**Q. Why do you want to manage things?**

**Q. What does 'done' mean?**

The word 'done' has multiple meanings. So we quote it as a 'Business' term.
A Business Term is a word used directly by the User in general speech about the topic. Keeping a list of these terms will help later.

***Refined Story 1***
```
As a person with things to be 'done'
I want to track and organise those things
so they get 'done' in priority order.
```

Playing the 5 whys game...

**Q. Why do you want to track them?**

***Refined Story 2***
```
As a person with things to be 'done'
I want to know what thing to do next
so they get 'done' in priority order.
```

Playing the 5 whys game...

**Q. Why do you want it ordered by priority?**

The word 'priority' has meaning. So we quote it as a Business term.

***Refined Story 3***
```
As a person with things to be 'done'
I want to know what thing to do next
so they get 'done' in 'priority' order.
```

Playing the 5 whys game...

**Q. Why do you say 'they' get done?**

***Refined Story 4***
```
As a person with things to be 'done'
I want to know what thing to do next
so things get 'done' in 'priority' order.
```

Playing the 5 whys game...

**Q. Why do you say 'thing'/'things' as opposed to 'task'/'tasks'?**

**A. 'Thing'/'Things' is conversational, we don't say to people, "I have tasks to do". Some phrases we might say are, for example, "I have stuff/things to do" or "I have something on".**

The word 'thing' has meaning. So we quote it as a Business term. The word 'thing' is an alias for 'stuff' or 'task'.

***Refined Story 5***
```
As a person with 'things' to be 'done'
I want to know what 'thing' to do next
so 'things' get 'done' in 'priority' order.
```

While the above is somewhat contrived we hope the idea is clear, to keep asking "why" until you feel you have got as many answers as you can.

In his book [Fifty Quick Ideas To Improve Your User Stories](https://www.amazon.com/Fifty-Quick-Ideas-Improve-Stories-ebook/dp/B00OGT2U7M) [Gojko Adzic](https://www.amazon.com/Gojko-Adzic/e/B004P9W8G6) provides great guidance for how to get better User Stories.

*** Business Terms ***

1. Done
2. Thing
3. Things
4. Priority

Some people who are proponents of Domain Driven Design (DDD) may say the Business terms are Domain terms and they are. We have avoided calling them Domain terms at this early stage because we have not yet started to model the Business, which comes after understanding the requirements/problem.
For example the Business Term 'Done' may require digging deeper into its meaning to the User.
