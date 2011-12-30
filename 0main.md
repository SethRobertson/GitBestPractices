Git Best Practices
========================================================

This is a fairly common question, and there isn't a One True Answer,
but still, this represents a consensus from #git


1. Read about git
----------------------------------

* [Pro Git](http://progit.org/book/)
* [Git for Computer Scientists](http://eagain.net/articles/git-for-computer-scientists/)
* [Git from the Bottom Up](http://ftp.newartisans.com/pub/git.from.bottom.up.pdf)
* [Git for Web Designers](http://www.webdesignerdepot.com/2009/03/intro-to-git-for-web-designers/ )
* [Other resources](http://git-scm.com/documentation)
* [Git wiki](http://git.wiki.kernel.org/)


1. Commit early and often
----------------------------------

Git only takes full responsibility for your data when you commit.  If
you fail to commit and then do something poorly thought out, you can
run into trouble.  Additionally, having periodic checkpoints means
that you can understand how you broke something.

People resist this out of some sense that this is ugly and might lead
to accusations of stupidity.  Well, I'm here to tell you that
resisting this is ignorant.  *Commit Early And Often*.  If, after you
are done, you want to pretend to the outside world that your work
sprung complete from your mind into the repository in utter perfection
with each concept fully thought out and divided into individual
concept-commits, well git supports that, see Sausage Making below.
However, don't let tomorrow's beauty stop you from performing
continuous commits today.

Personally, I commit early and often and then let the sausage making
be seen by all.  Just look at the history of this gist!


1. Don't panic
----------------------------------

As long as you have committed your work (or in many cases even added
it with `git add`) your work will not be lost for at least two weeks
unless you really work at it.

When attempting to find your lost commits, first make *sure* you will
not lose any current work.  You should commit or stash your current
work before performing any recovery efforts which might destroy your
current work.

There are three places where "lost" changes can be hiding. They might be
in the reflog (`git log -g`), they might be in lost&found (`git fsck
--unreachable`), or they might have been stashed (`git stash list`).

* reflog

    The reflog is where you should look first and by default.  It
    shows you each commit which modified the git repository.  You can
    use it to find the commit name (SHA-1) of the state of the
    repository before (and after) you typed that command.  While you
    are free to go through the reflog manually, you can also visualize
    the repository using the following command (Look for dots without
    children and without green labels):

    ````gitk --all --date-order `git log -g --pretty=%H`

* Lost and found

    Commits or other git data which are no longer reachable though any
    reference name (branch, tag, etc) are called "dangling" and may be
    found using fsck.  There are legitimate reasons why objects may be
    dangling through standard actions and normally over 99% of them are
    entirely uninteresting for this reason.

    * Dangling Commit

	These are the most likely candidates for finding lost data. A
	dangling commit is a commit no longer reachable by any branch or
	tag. This can happen due to resets and rebases and are
	normal. `git show SHA` will let you inspect them.

	The following command helps you visualize these dangling
	commits. Look for dots without children and without green labels.

	````gitk --all --date-order `git fsck --no-reflog | grep "dangling commit" | awk '{print $3;}'

    * Dangling Blob

	A dangling blob is a file which was not attached to a commit. This
	is often caused by `git add`s which were superceded before commit
	or merge conflicts. Inspect these files with `git show SHA`

    * Dangling Tree

	A dangling tree is a directory tree of files that was not attached
	to a commit. These are rarely interesting, and often caused by
	merge conflicts. Inspect these files with `git ls-tree -r SHA`

* Stashes

Finally, you may have stashed the data instead of committing it and
then forgotten about it.  You can use the `git stash list` command
or inspect them visually using:

````gitk --all --date-order `git stash list | awk -F: '{print $1};'`



1. Backups
----------------------------------

Take backups


1. Don't change published history
----------------------------------


1. Chose a workflow
----------------------------------

A standard workflow is best.

* Branch workflows

    Choosing the branch workflow helps you answer the following questions:

    * Where do important phases of development occur?
    * How can you identify (and backport) groups of related change?
    * What happens when emergency patches are required?

    See the following references for more information on branch
    workflows.

    However, also understand that everyone already has an implicit
    private branch due to their cloned repository: they can do work
    locally do a `git pull --rebase` when they are done, perform final
    testing, and then push their work out.  If you run into a
    situation where you might need the benefits of a feature branch
    before you are done, you can even retroactively commit&branch then
    optionally reset your primary branch back to @{u}.  Once you push
    you lose that ability.

* Distributed workflows

    Choosing a distributed workflow 


* Release workflow
* Security model
* Master repository


1. Dividing work into repositories
----------------------------------

* One concept per repository.
* Repository for large binary files
* Separate repository for continual changes to history
* Group concepts into a superproject

Use git-submodules or gitslave to group multiple concepts.


1. Useful commit messages
----------------------------------


1. Integration with external tools
----------------------------------

* Web views
* Bug tracking
* IRC/chat rooms


1. Keeping up to date
----------------------------------

Overlap with workflow.  Not everyone agrees with these ideas (but they
should!)

* Pulling with --rebase
* Rebasing (when possible)
* Merging without speeding


1. Periodic maintenance
----------------------------------

* Clean up your git repro every so often.
* Check your stash for forgotten work (`git stash list`)


1. Do
----------------------------------

* Experiment!  (in a clone)


1. Don't
------------------------------

In this list of things to *not* do, it is important to remember that
there are legitimate reasons to do all of these.  However, you should
not attempt any of these things without understanding

* Use git-grafts
* Use git-replace
* Rewrite public history
* Change where a tag points
* Use git-filter-branch
* Use clone --shared or --reference
* Use reset without committing/stashing
* Prune the reflog
* Expire "now"
* Commit configuration files

    Specifically configuration files which might change from
    environment to environment or for any reasons. See [Information
    about local versions of configuration
    files](https://gist.github.com/1423106)

1. Sausage Making
------------------------------

Some people like to hide the sausage making, or in other words pretend
that their commits 


1. Comments
------------------------------

Comments and improvements welcome.

Add them below, or discuss with SethRobertson (and others) on #git
