# git tips #

A collection of useful command line recipes for mastering source control with
git.

## What is the name of my current branch?

We all know that `git branch` gives us back the list of all local branches,
highlighting the branch our working copy is descendant from with an asterisk,
right?

	$ git branch
	* feature/some-funky-doo-dad
	  develop
	  master

When you only want to get back the name of the current branch, you can use
`git rev-parse --abbrev-ref HEAD` instead.

	$ git rev-parse --abbrev-ref HEAD
	feature/some-funky-doo-dad

## What was the date/time of a specific commit?

It might be useful to output just the date or time of a specified commit for
use in a shell script. To do this we can make use of the `git log --pretty`
switch, specifically with the "pretty formats" mode of operation.

	$ git log HEAD~1..HEAD --pretty=format:%ci
	2014-10-12 21:20:16 +1100

You might be satisfied by the UNIX time of the commit?

	$ git log -1 --pretty=format:%ct
	1413109216

Note we also used to different ways to refer to the same commit: `HEAD~1..HEAD`
is equivalent to `-1` in the second example.

There are other placeholders so you can construct almost any output here based
on commit metadata, see the full list in the [pretty
formats](http://git-scm.com/docs/git-log#_pretty_formats) documentation.
