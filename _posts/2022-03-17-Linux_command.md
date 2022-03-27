---
layout: post
title: Head First Git Summary 
tags: [Katex, Markdown]
---

**Efficient Linux at the Command Line Book by Daniel J. Barrett**

Table 3-1. Cursor keys for simple command-line editing
Keystroke	Action
Left arrow

Move left by one character

Right arrow

Move right by one character

Ctrl + left arrow

Move left by one word

Ctrl + right arrow

Move right by one word

Home

Move to beginning of command line

End

Move to end of command line

Backspace

Delete one character before the cursor

Delete

Delete one character beneath the cursor

**History Expansion with Carets**
Suppose you’ve mistakenly run the following command by typing jg instead of jpg:

$ md5sum *.jg | cut -c1-32 | sort | uniq -c | sort -nr
md5sum: '*.jg': No such file or directory
To run the command properly, you could recall it from the command history, cursor over to the mistake and fix it, but there’s a quicker way to accomplish your goal. Just type the old (wrong) text, the new (corrected) text, and a pair of carets (^), like this:

$ ^jg^jpg
Press Enter, and the correct command will appear and run:

$ ^jg^jpg
md5sum *.jpg | cut -c1-32 | sort | uniq -c | sort -nr
⋮
The caret syntax, which is a type of history expansion, means, “In the previous command, instead of jg, substitute jpg.” Notice that the shell helpfully prints the new command before executing it, which is standard behavior for history expansion.


**MORE POWERFUL SUBSTITUTION WITH HISTORY EXPANSION**
s/source/target/ The shell also supports a similar syntax. Begin with an expression for history expansion to recall a command, such as !!. Then add a colon, and end with a sed-style substitution. For example, to recall the previous command and replace jg by jpg (first occurrence only), just as caret notation does, run:


You may begin with any history expansion you like, such as !md5sum, which recalls the most recent command beginning with md5sum, and perform the same replacement of jg by jpg:

$ !md5sum:s/jg/jpg/
