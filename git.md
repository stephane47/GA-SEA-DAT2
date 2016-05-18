## Git config changes for DAT class repo

I've been pulling the class repo directly to my local machine so I can have easy access to class materials. However I've run into a few problems that it sounds like other people are having as well, so here are a few of the things I did to get it working smoothly. I set up my repo like Kevin suggested, so I'm typing `git pull upstream master` to update, where upstream is Jim's repo.

### Initial setup

Forked class repo on github
cloned my class repo to local machine
Setup local repo with `git remote add upstream https://github.com/JamesByers/GA-SEA-DAT2 `)
```
mbp13:GA-SEA-DAT2 stephane$ git remote -v
origin	https://github.com/stephane47/GA-SEA-DAT2 (fetch)
origin	https://github.com/stephane47/GA-SEA-DAT2 (push)
upstream	https://github.com/JamesByers/GA-SEA-DAT2 (fetch)
upstream	https://github.com/JamesByers/GA-SEA-DAT2 (push)
```
### Changes I've made in my workflow

We routinely edit notebook files in class. Before I open a notebook, I copy it into this folder (which I created), and open the copy. This way I can save any changes, but the original is unchanged so git doesn't complain. *If you copy them to a directory outside of the repo dir, you'll also have to copy the `data` and `images` dirs for some of the notebooks to work.*

This way I can keep my edited copies of notebooks, and also get Jim's updated versions, and they both work.

1. Create a new directory `mylocaldir` in your local repo
2. Copy Jim's notebooks to `mylocaldir`
3. Edit the repo's exclude file:

You have to tell git to ignore your new folder, as well as a few other files. You can do this by adding some lines to the `.git/info/exlude` file in your local repository:

Note: my repo is at
`/Users/stephane/classes/ds2/repos/GA-SEA-DAT2`...
so the file is...
`/Users/stephane/classes/ds2/repos/GA-SEA-DAT2/.git/info/exlude`

my `exclude` file looks like this:
```
# git ls-files --others --exclude-from=.git/info/exclude
# Lines that start with '#' are comments.
mylocaldir/
.DS_Store
.ipynb*
```
Note about the other 2 lines I added to this file:

2. `.ipynb*` When you open a notebook in Jupyter, even if you don't manually save an edited version, it will create an autosave file after a few minutes. This tells git to ignore those files too.

3. `.DS_Store` Git didn't like these files popping up either, which on a Mac is inevitable. Git ignores them now.


### Trouble with merges (OSX), getting dumped to a mystery screen in the terminal:

After entering the `git pull upstream master` command in a terminal window, you might see some activity, and then get dumped to a different screen that doesn't seem to respond to anything you do. What's happened is that git seems to think it needs you to make a local commit before it can complete the pull, and since you didn't enter a commit message, it dumps you into the default bash text editor which is `vi`. To get out of `vi` so that the pull can complete, hit 3 keys, one at a time: ':', 'x', 'enter'. If that doesn't work hit the `Esc` key and try it again. It should close the editor and let `git pull` complete.


