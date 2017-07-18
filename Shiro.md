


#### Subject
------

When you’re securing your application, probably the most relevant questions to ask yourself are: 
1. “Who is the current user?” 
2. “Is the current user allowed to do X”? 

It is common for us to ask ourselves these questions as we're writing code or designing user interfaces: applications are usually built based on user stories, and you want functionality represented (and secured) based on a per-user basis. 

The most natural way for us to think about security in our application is based on the current user. 
Shiro’s API fundamentally represents this way of thinking in its Subject concept.

##### What is a Subject ?
-------

This is the currently executing user (human being, 3rd party process, daemon account...). 
(It's just not called a 'User' because the word 'User' is usually associated with a human being).
'the thing that is currently interacting with the software'

