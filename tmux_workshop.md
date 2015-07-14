#What is a tmux?

Tmux is a terminal multiplexer, which basically means it's a way to have
multiple terminal sessions live inside of a single terminal window. This is
super handy! It lets us do things like:

![](example.png)

Here I have Vim open on the left, and on the right I have a shell up top
and a python interpreter on the bottom. Tmux lets me switch between all of
these 'panes' using the keyboard.

#Installing!

###Mac OS

To get tmux on Mac OS you need homebrew already installed, and then you
can just do:

    brew install tmux

should be it!

###Linux

I think tmux should be in the repos for just about every Linux distro (I
know it is for Arch and Debian).

#Configuration

To configure tmux we can put stuff in `~/.tmux.conf`. 


