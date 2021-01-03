# Markdown style guide

What's lovely about Markdown is the ability to write plain text and get nice
looking output as a result.  Wherever possible, your Markdown should be simple
and consistent within the whole corpus.

We seek to balance three goals:

1. _Source text is readable and portable_
2. _Markdown files are maintainable over time and across teams_
3. _The syntax is simple and easy to remember_

**Contents:**

1. [Doc layout](#doc-layout)
2. [Writing style](#writing-style)
	1. [Character line limit](#CHaracter-line-limit)
	2. [Trailing whitespace](#trailing-whitespace)
	3. [Double spacing](#double-spacing)
3. [Headings](#headings)
	1. [Add spacing to headings](#add-spacing-to-headings)
4. [Lists](#lists)
5. [Links](#links)
6. [Images](#images)
7. [Code](#code)
	1. [Inline](#inline)
	2. [Codeblocks](#codeblocks)

## Doc Style

```markdown
# Document Title

Short introduction

[TOC]

## Topic

Content.

## See also

* https://link-to-more-info
```

Let's break this down.

1. `# Document Title`: This heading should be a level 1 heading and ideally
					the same as the filename.
					This heading is typically used as the page title.
2. `Short introduction`: This should be 1-3 sentences that provides
					a high-level abstraction of the topic.
					The key to writing good introductions is to imagine
					yourself as a complete newbie and ask yourself questions.
					"What is this? Why should I use this?"
3. `[TOC]`: If you are writing a long page on a topic, you should include
		a table of contents such that newbies will be able to jump quickly to
		a specific section.  In some hosting platforms like Gitiles, putting
		`[TOC]` can automatically generate a table of contents based on the
		headings in the page.  Note: GitHub-flavored Markdown does not support
		this.
4. `## Topic`: The rest of the page's headings should start as level 2.
5. `## See also`: Put misc.  links at the bottom if the reader wants to
				know more or didn't find what they needed.

## Writing Style

### Character line limit

We, at BTHS SCT, like to wrap each line at 79 characters.
This is because it is the gold standard for coding since the age of teletypes.
You will find many languages such as Python and C that specify this limit.
We extend this to writing markdown files.  Although the output is the same
with or without the convention, it is still easier on the eyes of the writer
and editor.

You will find long URLs and tables to be the usual suspect of breaking
the rule (Headings also can't be wrapped, but we encourage keeping them
short).  Otherwise, wrap your text:

```markdown
Lorem ipsum dolor sit amet, nec eius volumus patrioque cu, nec et commodo
hendrerit, id nobis saperet fuisset ius.

* Malorum moderatius vim eu.  In vix dico persecuti.  Te nam saperet percipitur
  interesset.  See the [foo docs](https://textiles.dummycourse.com/somefile/someguide/somedocs/foo.md).
```

Often, inserting a newline before the link can preserve readability while
minimizing the overflow.

```markdown
Lorem ipsum dolor sit amet.  See the
[foo docs](https://textiles.dummycourse.com/somefile/someguide/somedocs/foo.md).
for details.
```

### Trailing whitespace

Don't use trailing whitespace.

Although the official ruling on whitespace is to insert two spaces at the
end of a line to create a break line, most hosting platforms don't
support it and many IDEs clean it up anyway.

Markdown creates paragraphs with newlines and thereby breaks text: get
used to that.

### Double spacing

As a writer, there is little benefit in producing two spaces after sentences.
That is not to say there is anything wrong with using two spaces after
sentences.  However, nearly all style guides agree that one space is correct.
The two-space convention was left over from the days of typewriters.
Typewriters allot the same amount of space for every character, so a narrow
character like _i_ gets as much as a wider character like _w_.  (This is called
a monospaced font.) With a typewriter, it makes sense to add an extra space to
make it clear that the sentence has ended.  With the popular introduction of
non-monospaced fonts by Steve Jobs, the two-space convention is meaningless.
Some would argue otherwise[¹](#references).

At BTHS SCT, we use double space: get used to it.

## Headings

This is fairly straight forward.
Headings are created using either the `#` character or the `---` characters.

Do this:

```md
## Heading 2
```

Not this:

```md
Heading - do you remember what level? DO NOT DO THIS
----------
```

### Add spacing to headings

Prefer spacing after `#` and newlines before and after:

```markdown
...text before

# Heading 1

Text after...
```

It's much easier to read this compared to this:

```markdown
...text before.

#Heading 1
Text after...  DO NOT DO THIS
```

## Lists

This is similarly straightforward.

```md
1. Foo.
	1. Foofoo
	1. Barbar
1. Baz.
```

Markdown is smart enough to let numbered lists like above render correctly.
Prefer numbered lists, because it's nicer to read in source:

```md
1. Foo.
2. Bar.
3. Baz.
```

Note: Please use tables when _absolutely_ necessary.  It is such a pain to
write tables in Markdown and they are not appealing in source.

## Links

It's a well known fact that long links make source Markdown hard to read
and break the 79 character limit.
**Wherever possible, shorten your links**

**Use informative Markdown link titles**

Markdown link syntax allows you to set a title to each link so that you shorten
the link and describe it.

Do not title your links with `here` or `link` or anything similar, it is not
descriptive and tells the reader nothing.

Instead, write the sentences naturally, then wrap with the most appropriate
phrase with the link.

Do this:

```md
See the [syntax guide](syntax_guide.md) for more info.
Or, check out the [style guide](style_guide.md).
```

Not this:

```md
See the syntax guide for more info: [link](syntax_guide.md).
Or, check out the style guide [here](style_guide.md).
DO NOT DO THIS.
```

## Images

Images are used sparingly, and are commonly simple screenshots.
If you use them sparingly and wisely, you'll find it is very helpful.

Note how the syntax includes an `!` to denote an image reference.
```md
![diffy the kung fu review cuckoo](http://commondatastorage.googleapis.com/gerrit-static/diffy-w200.png)
```

## Code

### Inline

Backticks (found on the `~` button near the top right of your keyboard)
designate `inline code`, and will render all wrapped content as is.
Use them for short code quotations and field names:

```
You'll want to run `really_cool_script.sh arg`.
Pay attention to the `foo_bar_whammy` field in that table.
```

They can also be used to suggest file types in an abstract sense, rather
than a specific file

```
Be sure to update your `README.md`!
```

### Codeblocks

For code quotations longer than a single line, use a codeblock:

``````
```python
def Foo(self, bar):
    self.bar = bar
```
``````

Note: To create this escaped code quotation, add more backticks to the
outer layer of backticks

**Declare the language**

It is best practice to explicitly declare the language, so that neither
the syntax highlighter nor the next editor must guess

**Indented codeblocks are sometimes cleaner**

Four-space indenting is also interpreted as a codeblock.
These look cleaner and are easier to read in source, but there is no way
to specify the language.
Use these indented codeblocks when writing short snippets like so:

```markdown
You'll need to run:

	bazel run :thing -- --foo

And then:

	bazel run :another_thing -- --bar

And again:

	bazel run :last_thing -- --baz
```

You can also do this in a list, be sure to indent it so as to not break the
list.

## See also

To get you familiar with the syntax, we recommend this 10 minute hands-on
[tutorial on markdown](https://www.markdownguide.org/basic-syntax/)

If you prefer to read about the specific Markdown we'll be using, this
[GitHub guide](https://guides.github.com/features/mastering-markdown/)
should get you started.

### References

1. ^ https://www.theatlantic.com/science/archive/2018/05/two-spaces-after-a-period/559304/
