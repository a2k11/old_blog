---
layout: post
title: The Power of Vim
---

### Vim and Tmux Commands

Vim is Vi Improved.  It is a text editor that is based off of vi which was a
text editor for unix based systems.  It is a free open source software which was
designed for use from a command line interface and a stand only application.  It
was first released in 1991 and has been updated 23 additional times.  For the
past 4 1/2 weeks I've been trying to become an efficient and productive vim
user.  It is difficult to not enter "INSERT" mode and correct all your mistakes
by using the up and down arrows.  You have to be patient with vim in order to
learn its power and it is very powerful.  Here is a list of the common commands
I use with vim as of right now and I hope to keep adding to this arsenal over
time.  

<pre><code>
VIM COMMANDS

vim (filename)         -->  open filename for edits
(space) + n + t        -->  new vim tab
(space) + p + (tab)    -->  view next tab
(space) + n + (tab)    -->  view previous tab
:!                     -->  mkdir
:e                     -->  newfile / mkdir
(ctrl) + p             -->  search for file
:%s/oldthing/newthing  -->  replace
gg                     -->  go to top
(shift) + g            -->  go to bottom
ciw                    -->  change inside of word
.                      -->  repeat change
==                     -->  align line correctly
= + (shift) + g        -->  align everything below
(shift) + j            -->  smash two lines together
(shift) + a            -->  go to end of line
e                      -->  go to the end of next word
w                      -->  go to the beginning of next word
:sort                  -->  sort the contents
:vs                    -->  split the vim window

TMUX COMMANDS

tmux -2                    -->  start tmux with darker color
(ctrl + a) + (shift + 5)   -->  create two terminal windows vertical
(ctrl + a) + (shift + ')   -->  create two terminal windows horizontal 

</code></pre>

I hope to add to this ever growing knowledge of commands.  It is
easier to learn by practicing editing files without ever touching your mouse.  I
like to think of it as a style of the experts which is my goal to become.
