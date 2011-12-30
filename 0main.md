Git Best Practices
========================================================

This is a fairly common question, and there isn't a One True Answer,
but still, this represents a consensus from #git


1. Don't panic
----------------------------------

Tools, resources, reflog and other locations for missing data


1. Backups
----------------------------------

Take backups


1. Chose a workflow
----------------------------------

A standard workflow is best.

1.1. Branch workflows
1.1. Distributed workflows
1.1. Security model
1.1. Master repository


1. Dividing work into repositories
----------------------------------

1.1. One concept per repository.

1.1. Repository for large binary files

1.1. Separate repository for continual changes to history

1.1. Group concepts into a superproject

Use git-submodules or gitslave to group multiple concepts.


1. Useful commit messages
----------------------------------


1. Integration with external tools
----------------------------------

1.1. Web views
1.1. Bug tracking
1.1. IRC/chat rooms


1. Keeping up to date
----------------------------------

Overlap with workflow.  Not everyone agrees with these ideas (but they
should!)

1.1. Pulling with --rebase
1.1. Rebasing (when possible)
1.1. Merging without speeding

1. Cleaning
----------------------------------

Clean up your git repro every so often.
