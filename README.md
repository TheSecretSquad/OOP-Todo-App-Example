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
Try to talk to the end User whenever possible. It is solving their problem that is the key.

See [this post](https://www.linkedin.com/pulse/when-five-whys-dont-work-kylie-savage) as a good example of solving a problem but causing another for the actual User / Customer.

***Initial Story***
```
As a person with things to be done
I want to manage those things
so they get done
```

The single **most important step** a developer can do is to fully understand the requirements. We use the term requirements not interchangeable with the term problem. Ideally you are given a problem but this rarely happens so you need to dig deeper to fully understand the problem.
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

***Business Terms***

1. Done
2. Thing
3. Things
4. Priority

Some people who are proponents of Domain Driven Design (DDD) may say the Business terms are Domain terms and they are. We have avoided calling them Domain terms at this early stage because we have not yet started to model the Business, which comes after understanding the requirements/problem.
For example the Business Term 'Done' may require digging deeper into its meaning to the User.

### Further Questions for the User
Below are more questions we ask the user to elicit information about what the problem is. "Answers" are assumed to be from the User. Again, we are playing the role of the User.

**Q: Why do you want a digital list? Why do we need an App at all?**

***A: It's hard to keep 'things' in sync manually and I don't always remember a note pad and it's hard to change 'priority' with a physical list. Sometimes I want to 'share' the list with 'others'.***

**Q: Why is it hard to keep in sync manually? Can you show me how you do it?**

***A: &lt;In this case we expect the user would show us how they perform the task.&gt;***

**Q: Why do you want to 'share' the list with 'others'?**

***A: So 'others' can see what I am doing.***

**Q: Would todo list still be usable if not 'shared' with 'others'?**

***A: Yes. May need to share later.***

**Q: What do you do when you have a new 'thing' for the list?**

***A: I add the 'thing' to the list in 'priority' order.***

**Q: What do you do when the 'thing' is done?**

***A: I put a line through the 'thing'.***

**Q: What happens when a 'thing' that is done is actually not done?**

***A: I add the 'thing' again in 'priority' order.***

**Q: What happens when the 'priority' changes for a 'thing'?**

***A: I cross out the current 'priorities' and make new ones.***

**Q: What happens when the list gets really long?**

***A: It doesn't get that long because I make a new list each day with only the 'things' that are not 'done'.***

**Q: What do you do when you start a 'thing'?**

***A: I just do it. I don't update the list until it is 'done'.***

**Q: Would it be helpful to mark 'things' that you're doing?**

***A: Not for myself, but yes if the list is 'shared' with 'others'.***

You might be thinking _get to the code already_ and we will but to reiterate, 
the single most important step a Developer can take is to understand the requirements as best they can.

***A Refined Story 6***
```
As a person with 'things' to be 'done' 
who has trouble keeping them in 'sync' manually
I want to know what 'thing' to do next 
so 'things' get 'done' in 'priority' order.
```

The differences in Refined Story 6 and Refined Story 5 could be separated out, 
especially if you feel Story 5 and Story 6 represent different problems or could be delivered separately.

We have also chosen to ignore the sharing of 'things' with others for now. 
We will come back to this part if the problem later.
 
From here we would also play the "5 Why's Game again, however you get the point so we will move on.
We also discovered a new Business term 'Sync' which was used by the User.

***Business Terms***

1. Done
2. Thing
3. Things
4. Priority
5. Sync

As a disclaimer, we the authors are not saying we are experts at story writing, nor are we saying the 
story so far is the best example. 
However, we are saying that doing something to discover the real problems faced by real users is the first and most
important step you can take.

You may be in a situation where the story or other detail is provided to you. In these cases you should still 
play the "5 Why's Game" to uncover any gaps in the detail provided.

 