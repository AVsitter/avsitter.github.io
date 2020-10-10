---
title: Contributor Guidelines
summary: The AVsitter Project is open-source and welcomes help from the community.
keywords: mydoc
sidebar: home_sidebar
toc: false
permalink: contribute.html
folder: contribute
---

## Scripting contributions

- Script contributions should be submitted via pull request on the [AVsitter GitHub repository](https://github.com/AVsitter/AVsitter).
- There is a link message guide for AVsitter2 [here](https://github.com/AVsitter/AVsitter/blob/2.2r04/AVsitter2/avsitter2_link_message_reference.md).
- AVsitter LSL scripts are licensed under the [Mozilla Public License Version 2.0](https://www.mozilla.org/en-US/MPL/2.0/) and must include the following header:
<pre>/* This Source Code Form is subject to the terms of the Mozilla Public
 * License, v. 2.0. If a copy of the MPL was not distributed with this
 * file, You can obtain one at http://mozilla.org/MPL/2.0/. */</pre>

## Documentation contributions

- Documentation improvements should be submitted via pull request on the [GitHub repository for AVsitter Documentation](https://github.com/AVsitter/avsitter.github.io).
- AVsitter Documentation uses the [Jekyll Documentation Theme](http://idratherbewriting.com/documentation-theme-jekyll/mydoc_pages.html) ([see template guidelines](/mydoc_introduction.html)).
- AVsitter Documentation is released under the [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) license.
- LSL example scripts provided in the AVsitter Documentation are released under the [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/) license.

## Contributor guidelines for Commits in Pull Requests

- Commits should change one "atomic feature" at a time so that the repository is in a working state after every commit, but trying to avoid commits that make several unrelated changes. There are several purposes: to ease review by others to ensure there are no new problems, to ease checking the history and to ease rolling back a commit, should that be necessary. Do not squash commits.

- The commit message should describe the change as best as possible. The first line is the title and should summarize the commit in about 70 chars if possible; if more explanations or some clarifications are necessary, leave a blank line under the title and add the details below that.

- Indentation and formatting changes cause very messy diffs, because they tend to sync with the wrong lines. It's best to separate those changes from the functionality-changing ones, while announcing that there are no code changes otherwise, in order for the reviewer to focus on what's important without having to decipher the messy diffs.

- Sometimes, while making a change we spot a part of the code that needs an unrelated change, and we go ahead and fix it before we forget. For those cases, git provides the `-p` flag for the `commit` and `add` commands, which allows selecting which changed lines go into the commit and which ones don't, or even editing the diff of what goes into the commit. To avoid mixing unrelated changes, you can make use of that.

- File renames should have their own separate commit. Don't rename and change a file in the same commit; otherwise it's nearly impossible to see what changed.

- For small amendments to the PR prior to being reviewed, e.g. something that was overlooked in one of the commits, it’s best to amend the commits as necessary and force-push. But if the code has already been reviewed, submit it as new commit(s) instead, unless instructed otherwise. This will allow the reviewers to easily check what exactly has changed between the changes that were already reviewed and the new ones, without needing to go over the full set of changes. If the original changes were small and the new ones are assumed to be small, or cover the majority of the other ones, the reviewer may choose to indicate to amend the commit instead.

### Guidelines for those with Commit access

- In order to ease checking the history and to ease rolling back a commit, it's best if PRs (Pull Requests) are not squashed. We can use "Rebase and merge", though "Merge" would work as well.

- Pull requests should preferably be merged only after they have been greenlighted by at least two developers. This may change to mandatory in future as we have more developers, and the number may change to three depending on the size of the team.

