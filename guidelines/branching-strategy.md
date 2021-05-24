Gitflow is the default branching strategy for all Global BIA projects. The default ADO build pipeline will assume that the project has this structure.

Git flow workflow - Hotfix Branches

All new repositories should have a master and develop branch at the minimum.

**New Feature**

New features should get branches named "feature/12345-Feature-Name" where 12345 is the ADO user story/task number and Feature-Name is a high level descriptor of the feature. As shown in the diagram above, these feature branches should only be based on the develop branch.

When features are completed, a pull request should be opened to merge these into the develop branch. At least one project owner/reviewer should approve this PR before merge.

**New Release**

Release branches should be named like "release/1.0.0" and be branched from the develop branch. When release branches are completed they should be

1. Merged into master, which will trigger deployment ADO pipeline.
2. Merged into develop, in case pre-release changes were made.

At least one project owner/reviewer should approve these PR before merge.

**Hotfixes**

In case a change is needed to a release that has already been pushed to master, a hotfix branch can be used and merged back into master/develop on completion. This should be avoided as much as possible.
