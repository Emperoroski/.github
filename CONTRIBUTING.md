# Contributing to RSocket

:+1::tada: First off, thanks for taking the time to contribute! :tada::+1:

This document gives you guidelines and pointers at how you should approach contributing.
Links to eg. create issues point to `rsocket/rsocket-java` repository. Amend this depending on the actual project you're targetting (eg. `rsocket-js`, `rsocket-java`, `rsocket-cpp`...).

Start here:

 - [Do you have a question?](#question-do-you-have-a-question)
 - [Did you find a bug?](#beetle-did-you-find-a-bug)
 - [Did you write a patch that fixes a bug?](#wrench-did-you-write-a-patch-that-fixes-a-bug)
 - [Do you intend to add a new feature or change an existing one?](#mag-do-you-intend-to-add-a-new-feature-or-change-an-existing-one)
 - [PR and commit style](#sparkles-pr-and-commit-style)
 - > be sure to at least look at the [Commit Message Convention](#black_nib-commit-message-convention)
 - [More details](#speech_balloon-more-details)
 - [Learning more about the tools we use](#mortar_board-learning-more-about-the-tools-we-use)

The RSocket team appreciates your contributing effort! :heart: :heart: :heart:

## :question: Do you have a question?

> Search Stack Overflow first; discuss if necessary

If you're unsure why something isn't working or wondering if there is a better
way of doing it please check on **Stack Overflow** first and if necessary start
a discussion. Use relevant tags among the ones we monitor for that purpose:
 - [`rsocket`](https://stackoverflow.com/questions/tagged/rsocket) for generic rsocket questions
 - `rsocket-xxx` for specific rsocket implementation in particular language questions (where `xxx` stands for a short name of the language such as `js`, `java`, etc.)

If you prefer real-time discussion, we also have a few **Gitter channels**:
 - [`rsocket`](https://gitter.im/rsocket/rsocket) specification questions and disscussions  
 - [`rsocket-community`](https://gitter.im/rsocket/community) all community questions
 - [`rsocket-java`](https://gitter.im/rsocket/rsocket-java) rsocket-java related questions

Refer to each project's README for potential other sources of information.


## :beetle: Did you find a bug?

 - **Do not open a GitHub issue if the bug is a security vulnerability in RSocket** (see [SECURITY.md](https://github.com/rsocket/.github/blob/master/SECURITY.md))
 - **Ensure the bug was not already reported**: Do a bit of searching
the relevant project's **Issues** (eg. [rsocket-java Issues](https://github.com/rsocket/rsocket-java/issues/)) to see if you
can find something similar
 - If you don't find something similar, **open a new issue** (eg. [rsocket-java new issue](https://github.com/rsocket/rsocket-java/issues/new)).
 Be sure to follow the template and to include a title and clear description.
 Add as much relevant information as possible, and a code sample or an executable test case demonstrating the expected behavior that is not occurring

## :wrench: Did you write a patch that fixes a bug?

 - _Unless the fix is trivial_ (typo, cosmetic changes that don't modify the behavior, ...), there **should be an issue** associated with it.See [Did you find a bug?](#beetle-did-you-find-a-bug).
 - Wait for **issue triage** before you start coding. This will determine from which branch to start. See [Starting from the right branch](#starting-from-the-right-branch) section for more details
 - Try to create a branch with a **meaningful name** (see hints [here](#creating-a-branch-with-representative-name))
 - Work on your change. Be sure to include **JUnit test cases**, this will greatly help maintainers while reviewing your change
 - **Formate your code** prior to submission: (eg. for RSocket-Java it can be `./gradlew goJF`)
 - **Run all tests locally** prior to submission: (eg. for RSocket-Java it can be `./gradlew check`)
 - Finally, you're **ready to submit** your Pull-Request :+1:

## :mag: Do you intend to add a new feature or change an existing one?
 - Again, **search for similar suggestions** in existing issues (including closed ones)
 - If nothing like that has been suggested before, **discuss it in a new issue first**
 - If you gather positive feedback, **work on the change** following the guideline [above](#wrench-did-you-write-a-patch-that-fixes-a-bug)

## :sparkles: PR and commit style

 - **Commit early and commit often**. Try to still have **descriptive commit messages** though. This helps during the review process, to see through which steps and train of thought you went
 - Once submitted, the review and discussion starts. If necessary, make adjustments in **further commits**
 - Use your **real name** in commits (see [configuration hints](#using-real-names))
 - _Once the PR is **approved**_ :white_check_mark: , clean up and **prepare for merge** (see [From PR to master](#from-pr-to-master))

### From PR to `master`
For each PR, there will generally be **a single commit** that goes into `master`. We will try to use the `squash-and-merge` strategy on GitHub to that effect, but if you do that yourself once the PR is approved, it's even better :heart:

Another case where your help is needed in preparing for merge is **if your PR has a few logical changes**, and you'd like to have as many commits.
(Note that if you have more than, say, 3 of these, it's probably that you actually need to do several PRs).
If you want us to rebase-and-merge, you'll need to let us know and to perform a manual `git rebase -i BASE_BRANCH` in order to prepare the commits.
You'll probably need to at least squash intermediate commits from the "commit early and often" side of things, and to ensure that the final commits all follow the message convention.

TL;DR: as a maintainer, use `git merge --no-ff --no-commit 1.0.x` and `Merge #xxxx into 1.1` (where `1.0.x` is the maintenance branch and `1.1` is the current generation). Once done, add 👍 or 🚀 on the bot's message.

We tend to put the oldest maintenance branch as the milestone of the issue and the newest milestone in which it was forward merged as the milestone of the pr (when there is both an issue and PR).  
If there is only a PR, use the oldest milestone in which it will be released.


### :black_nib: Commit Message Convention
We use the following convention for commit message title and body:

```
PREFIX DESCRIPTION

Longer description of the content of the commit and/or context of the
changed, hard-wrapped at 72 characters
```

 - `PREFIX` is either a `[TAG]` or a more conventional `fix #ISSUE`:
    - `[TAG]` is for smaller commits that don't have an issue. We notably use `[test]` for test amendments, `[doc]` for small docs changes like typos, `[build]` for fixes to the CI configuration.
    - most of the time, there should be an issue referenced instead. We prefix with the keyword `fix` so that GitHub will close the issue once the PR is merged. If the PR is a preparation or a follow-up, use `see #ISSUE` instead (eg. `fix #1226` vs `see #1226`). 
 - `DESCRIPTION` should be a short but meaningful description of the fix, preferably under 50 chars (the whole title line should NOT go over 72 chars)


## :speech_balloon: More details

### Starting from the right branch

Issues are useful before opening a pull-request because they allow the RSocket
team to do some triage, answer questions and help with designing a fix.

Additionally, during the triage process the team will evaluate the criticality
of the reported issue and decide wether or not it should also be fixed in current
maintenance branche(s).

If this is the case, the fix should be implemented against the earliest relevant
maintenance branch, which will be indicated in the issue as the _milestone_.

For instance, if an issue should be fixed in both 1.0 and 1.1, the later being
developed on master, the fix PR should be opened against `1.0.x` (and the issue
will be triaged into `1.0.x Maintenance Backlog`).

If on the other hand the issue should only be fixed in the next feature release,
it will be affected to the `Backlog` triage milestone and should be developed
against `master`.

### Creating a branch with representative name

Branches used when submitting pull requests should preferably be named
according to the `xxx-shortDescription` convention:

 - `xxx` is the github issue number
 - use a `-` separator, at least after issue number
 - `shortDescription` should be a few representative words about the issue
 
For example: `1226-lastOnEmptyCallable`.


### More about commits

#### Message convention
Here is a more detailed example of the commit message convention:

```
    fix #ISSUE Prefer short (50 chars) summary of changes

    More detailed explanatory text, if necessary. Wrap it to about 72
    characters or so. In some contexts, the first line is treated as the
    subject of an email and the rest of the text as the body. The blank
    line separating the summary from the body is critical (unless you omit
    the body entirely); tools like rebase can get confused if you run the
    two together.

    Further paragraphs come after blank lines.

     - Bullet points are okay, too

     - Typically a hyphen or asterisk is used for the bullet, preceded by a
       single space, with blank lines in between, but conventions vary here

    Related Issues: #1234, gh-1235
```


1. Use imperative statements in the subject line, e.g. "Fix broken Javadoc link".
1. Begin the DESCRIPTION with a capitalized verb, e.g. "Add, Prune, Fix,
    Introduce, Avoid, etc."
1. Prefix the subject line with "fix #XXX " if the commit is fixing issue XXX (or
    replace "fix" with "see" if it is only related to an issue without closing it)
1. Do not end the subject line with a period.
1. Restrict the subject line to 72 characters or less.
1. Wrap lines in the body at 72 characters or less.
1. In the body of the commit message, explain how things worked before this
    commit, what has changed, and how things work now.

#### Using real names
Please configure git to use your real first and last name for any commits you
intend to submit as pull requests. For example, this is not acceptable:

    Author: Nickname <user@mail.com>

Rather, please include your first and last name, properly capitalized, as
submitted against the Spring Individual Contributor License Agreement (ICLA):

    Author: First Last <user@mail.com>

This helps ensure traceability against the ICLA and also goes a long way to
ensuring useful output from tools like `git shortlog` and others.

You can configure this via the account admin area in GitHub (useful for
fork-and-edit cases); _globally_ on your machine with

    git config --global user.name "First Last"
    git config --global user.email user@mail.com

or _locally_ for the specific branch. E.g. for `rsocket-java` repository only you may do that by omitting the
'--global' flag:

    cd rsocket-java
    git config user.name "First Last"
    git config user.email user@mail.com

#### Add Apache license header to all new classes

```java
/*
 * Copyright 2015-Present the original author or authors.
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *     http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */

package ...;
```

#### Update Apache license header in modified files as necessary

Always check the date range in the license header. For example, if you've
modified a file in 2019 whose header still reads:

```java
/*
 * Copyright 2015-2017 the original author or authors.
 */
```

Then be sure to update it to:

```java
/*
 * Copyright 2015-Present the original author or authors.
 */
```


## :mortar_board: Learning more about the tools we use

### Pull-Requests
Not sure what a pull request is, or how to submit one? Take a look at GitHub's
excellent [help documentation](https://help.github.com/categories/collaborating-with-issues-and-pull-requests/) first.

Follow the same conventions for pull request subject lines as mentioned above
for commit message subject lines.

In the body:

1. Explain your use case. What led you to submit this change? Why were existing
   mechanisms in the framework insufficient? Make a case that this is a
   general-purpose problem and that yours is a general-purpose solution, etc.
1. Add any additional information and ask questions; start a conversation or
   continue one from the original GitHub issue.
1. Mention the Github issue ID if there is one.

Note that for pull requests containing a single commit, GitHub will default the
subject line and body of the pull request to match the subject line and body of
the commit message. This is fine, but please also include the items above in the
body of the request.

### Squashing Commits
To learn more about these techniques, like `git rebase --interactive --autosquash`,
`git add --patch`, and other tools to "squash" multiple commits into a single
atomic commit, in addition to the man pages for git.
The [Rewriting History section of Pro Git](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)
provides a good overview about these tools.
