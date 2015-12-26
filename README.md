# Tortoise HG to GitHub #

## Overview ##

Information on how to set up Tortoise Hg to push to GitHub

These are from personal experience, YMMV.

## Requirements

- A GitHub account
- hg-git from [http://hg-git.github.io/](http://hg-git.github.io/ "http://hg-git.github.io/")


## Steps

1. Install or enable hg-git. Check your thg ui, it may be already installed.
2. Create an hg repo on a directory and do a first commit, or you can use an existing directory.
3. Run the command `hg bookmark -r default master` This will set the master bm to be default, so a ref gets created. Evidently a GitHub requirement.
4. Create a new repo on GitHub.
5. Copy the GitHub repo https from the repo you made ~ `https://github.com/<user>/<repo>.git`
6. Add the following to your hg repo settings file:

`[paths]`<br/>
`default=git+ssh://git@github.com/MarkRobbins/hggit_vpw.git`

`[ui]`<br/>
`#optional, use plink/pagent`<br/>
`ssh = "TortoisePlink.exe"`

`[hooks]`<br/>
`#optional, push on commit`<br/>
`post-commit.autopush = hg push`

Then you can do a push and/or may push on local commits

Do another commit then move the `master` bookmark to `tip` by right clicking on `tip` in hg workbench and selecting *bookmarks*

After that, `master` should keep up with `default/tip`

## Caveats / Shortcomings

- You do not want to use both Git and Hg in the same repo, one will always be out of sync.
- There are many unknown unknowns about this, at least AFAIK - its best to have reduced expectations. 

## References

[http://www.ryadel.com/en/using-github-with-mercurial-and-tortoisehg/](http://www.ryadel.com/en/using-github-with-mercurial-and-tortoisehg/ "http://www.ryadel.com/en/using-github-with-mercurial-and-tortoisehg/")
