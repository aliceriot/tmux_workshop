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

To configure tmux we can put stuff in `~/.tmux.conf`. As a quick example
let's add mouse support! We do:

    set-window-option -g mode-mouse on
    set-option -g mouse-select-pane on
    set-option -g mouse-select-window on
    set-option -g mouse-resize-pane on
    setw -g mode-mouse on

Keybindings are great, but mouse support is sometimes super handy!

#Create a tmux session

If you want to start tmux we do:

    tmux new

If you run this in a terminal you'll probably get a bar drawn along the
bottom, but otherwise it will be pretty unexciting.

We can give our tmux session a name by doing:

    tmux new -s 'name'

This will come in handy later! On my machine I always name my tmux
instances, so I use this alias a lot:

    alias new='tmux new -s'

then I just do `new python` or `new todo` or some such thing. Nice!

#Command Prefix

Tmux is controlled mostly from the keyboard. Although we enabled mouse
support above, we can't use the mouse to make new panes or windows. If we
want to enter a command in tmux we first hit the `prefix` keybind, which
by default is `ctrl-b`. I don't particularly like this, so I have mine
bound to `ctrl-w`, but you can do whatever you like! Some folks use
`ctrl-a`, but this interferes with readline.

To bind a custom prefix:

    unbind C-b #get rid of the default
    set -g prefix C-w
    bind C-w send-prefix

And that's it! `C` is tmux-speak for `ctrl`.

#Detaching and Attaching

One of the coolest features of tmux is that we can 'detach' from a running
tmux session, and it will continue to run in our absense. To detach we do
`prefix-D`, which means hit prefix, release the keys, and then type
`shift-D`. Cool! This is sort of like using `C-z` to suspend Vim, but we
could be suspending a whole number of virtual terminals. Nifty!

On a related note we can get a list of running tmux sessions by doing:

    tmux list-sessions

this is why I like to name them: if the tmux sessions have names then it's
easier to tell them apart if you have multiple ones running (I usually do
because I'm messy).

We can also reattach to a running session by doing:

    tmux attach -t 'session name'

I have this aliases to `attach`. This will plop us back into the tmux
session we started earlier, and everything we had open will still be
there.

This is super super handy! Where tmux becomes really useful is when
interacting with other computers over ssh: if you're doing your work in
a tmux session you don't need to fear network problems! If your ssh
connection is interrupted you will be able to reattach right back where
you were.

This also applies to accidentally closing a terminal window on your
machine!


