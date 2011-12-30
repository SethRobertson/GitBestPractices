Git Best Practices
========================================================

This is a fairly common question, and there isn't a One True Answer,
but still, this represents a consensus from #git


[panic] 1. Don't panic
----------------------------------

Tools, resources, reflog and other locations for missing data


[backups] 1. Backups
----------------------------------

Take backups


[workflow] 1. Chose a workflow
----------------------------------

A standard workflow is best.

* Branch workflows

    Choosing the branch workflow helps you answer the following questions:

    * Where do users make changes?
    * How can you identify (and backport) groups of related change?

* Distributed workflows
* Security model
* Master repository


[division] 1. Dividing work into repositories
----------------------------------

* One concept per repository.
* Repository for large binary files
* Separate repository for continual changes to history
* Group concepts into a superproject

Use git-submodules or gitslave to group multiple concepts.


[commit_messages] 1. Useful commit messages
----------------------------------


[integration] 1. Integration with external tools
----------------------------------

* Web views
* Bug tracking
* IRC/chat rooms


[merging] 1. Keeping up to date
----------------------------------

Overlap with workflow.  Not everyone agrees with these ideas (but they
should!)

* Pulling with --rebase
* Rebasing (when possible)
* Merging without speeding

[cleaning] 1. Cleaning
----------------------------------

Clean up your git repro every so often.
