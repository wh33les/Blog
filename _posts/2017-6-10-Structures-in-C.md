---
layout: post
title: Structures in C
---
I am working on a page that lists each of the following data structures
* array list/vector
* linked list
* queue
* stack
* hashtable
* binary search tree
* priority queue/heap

along with an example in C, pros/cons, when to use, how to implement, big-O properties of basic operations, e.g., find, add, remove.  This exercise is based on a suggestion by @jw0 as part of my preparation for a Google interview.  Much of the information above I'm learning from Chapter 3 of Skiena's _The Algorithm Design Manual, 2nd Ed._  

Yesterday I wrote a C snippet illustrating an array.  In it, comments in all caps represent unseen blocks of code that are not the emphasis of the example.  The snippet prompts a user for 10 digits between 0 and 9, and then prints them as an array.
<img src="https://wh33les.github.io/images/naiveCExampleOfArray.png" title="naïve C" class="wrap align-left" height="60%" width="60%">
In retrospect this snippet seems pretty naïve, now that I've today refamiliarized myself with the <code>typedef</code> command, and the idea of structures.  My primary reference for C has been my old textbook from college, _Computer Science: A Structured Programming Approach Using C, 2nd Ed._ by Forouzan & Gilberg.  I took this course in the spring of 2006 so needless to say, I'm pretty rusty on C.  Evidently we did cover structures at the end of the course.  I totally didn't remember this until I saw all the blocks of highlighted text (this is how I "took notes" back then) when I opened the book.  Granted, we covered pointers about halfway through the course, which I do remember, in that I remember not understanding what the hell the point is of using pointers.  

Since Skiena conveniently writes examples of algorithms in C, I've had a chance to compare styles between the two texts.  Here is Skiena's example of a singly-linked list:
```C
typedef struct list {
  item_type item;        /* data item */
  struct list *next;     /* point to successor */
} list;
```
