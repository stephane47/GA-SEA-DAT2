## Git config changes for DAT class repo

I've been pulling Jim's repo directly on my local machine so I could have easy access to class materials. However I ran into a few problems that it sounds like other people are having as well, so here are a few of the things I had to do to get it working smoothly:

### Edit the repo's exclude file

I added the following lines to my `.git/info/exlude` file in the repository:

Ex: my repo is at
`/Users/stephane/classes/ds2/repos/GA-SEA-DAT2`...
so the file is...
`/Users/stephane/classes/ds2/repos/GA-SEA-DAT2/.git/info/exlude`

```
mylocaldir/
.ipynb*
.DS_Store
```

Explanation of each line: 

1. `mylocaldir/`
We routinely edit notebook files in class. Before I open a notebook, I copy it into this folder, and open the copy. This way I can save any changes, but the original is unchanged so git doesn't complain. *If you copy them to a directory outside of the repo dir, you'll also have to copy the `data` and `images` dirs for some of the notebooks to work.*

2. `.ipynb*` When you open a notebook in Jupyter, even if you don't manually save and edited version, it will create an autosave file after a few minutes. This tells git to ignore those files too.

3. `.DS_Store` Git didn't like these files popping up either, which on a Mac is inevitable. Git ignores them now.
