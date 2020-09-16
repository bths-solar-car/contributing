# Coding Style

This is a short document describing the preferred coding style for the Brooklyn
Technical High School Solar Car.  Everyone has a personal coding style, and I'm
not one to **force** my style on anyone, but it is necessary for maintenance.


## I. Whitespace

All indentation is to be done with tabs.  Tabs are defined as 8 characters.
There are groups that will define tabs as 4 characters (or even 2), but it
defeats the purpose of indentation.  The premise behind indentation is to
clearly define blocks of code.

There are some that will argue 8-character indentation makes code difficult to
read.  The answer to that is that if you need more than 3 levels of
indentation, you're doing it wrong, and should fix your program.

When trying to ease indentation in a switch statement, it is preferred to align
the `switch` with its subordinate `case` labels.

> Example:

```c
switch (condition) {
case 'A':
case 'a':
	x <<= 1;
	break;
case 'B':
case 'b':
	x <<= 2;
	break;
default:
	break;
}
```

Spaces are never to be used for indentation outside of comments.  Any use of
spaces for alignment purposes is permitted, but leave no trailing whitespace.


## II. Breaking Long Lines

The preferred maximum line length is 80 characters.  This is not a hard limit,
however it is done to maintain readability.

Where possible, statements that take up more than 80 characters should be
broken into sensible chunks, unless it significantly decreases readability.

Never break user-visible strings, this will break the ability to grep for them.

In short, the 80 character limit is a *recommendation*.
