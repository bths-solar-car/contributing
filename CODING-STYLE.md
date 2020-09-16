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


## III. Brace Placement

In a language like C, brace placement doesn't really matter, and there is no
reason to use one placement style over another.  That being said, the preferred
style is to put opening braces at the end of a line, and closing braces at the
beginning.

> Example:

```c
if (x) {
	y = returnSomething();
	x -= 2;
}
```

This applies to all non-function statement blocks (`if`, `switch`, `for`,
`while`, `do`).

> Example:

```c
for (int i = 0; i < 4; i++) {
	dest[2, i] = source[i];
	++source[i];
}
```

However, the only exception to this rule are functions: they have the opening
brace at the beginning of a new line.  This may seem inconsistent, but it makes
functions far more pronounced.

> Example:

```c
int main(int argc, char *argv[])
{
	body of function
}
```

Closing braces are always at the beginning of an empty line, **except** when
followed by a statement like `else` or `while` in a do-statement.

> Example:

```c
if (x != y) {
	..
} else if (x >= y) {
	...
} else {
	....
}
```

```c
do {
	body of loop
} while (condition);
```

Do not use braces for a single statement.

> Example:

```c
if (condition)
	action();
```

```c
if (condition)
	doThis();
else
	orThis();
```

However, this does not apply when only one branch of a conditional statement has
a single statement.

> Example:

```c
if (condition) {
	doThis();
} else {
	orThis();
	andThat();
}
```
