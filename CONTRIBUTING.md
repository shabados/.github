# Contributing to Shabad OS

Thank you for your interest in participating! This document caters to developers or programmers that wish to write code and directly contribute to the source code of Shabad OS. See [Feedback](#feedback) for non-developer contributors.

## Feedback

There are many ways for people to contribute, beyond writing code or programming:

* Ask a question via [Slack](https://chat.shabados.com)
* Request a new feature or report unexpected bugs by filing an issue
* Upvote popular feature requests using the thumbs-up/+1 reaction on the first post of an issue
* Follow [@shabad_os on Instagram](https://www.instagram.com/shabad_os/) and [@shabad_os on Twitter](https://www.twitter.com/shabad_os/) and let us know what you think!

## Prerequisites

If you wish to better understand how Shabad OS works or want to debug an issue: get the source, build it, and run it locally. 

## Workflow

We follow a _fork and pull model_. Our basic workflow of development is to choose an issue to work on, create a personal branch off `dev`, and submit a pull request.

### Issues

After getting started with the repo, check out the issues list:

* Issues labeled with `Impact: Crit` or `Status: 3hard5me` are good issues to submit a PR for.
* Issues labeled `Effort: 0` or `Effort: 1` are great if you are in the code for the first time.
* If you are contributing significant changes, please discuss with the assignee of the issue before beginning your work.


Check out the issue tracker for a list of all potential areas for contributions. Note that, just because an issue exists, does not mean we will accept a contribution for it. 

There are a few labels worth noting:

* _Effort: 0-109_ - The perceived/estimated "points" of effort to resolve the issue (points = hours)
* _Impact: {Low, Avg, High, Crit}_ - The perceived percentage of users the issue affects
* _Status: 3hard5me_ - Issues the assignee needs help to resolve

If an issue is easy to resolve and impacts a majority of users, then its resolution should be prioritized higher.

IMPORTANT: Be sure to discuss with the assignee of the issue, before tackling issues. If there are no assignees, ask to be assigned in a comment.

IMPORTANT: To avoid multiple pull requests resolving the same issue, let others know you are working on it by saying so in a comment.

### Branches

The `master` branch is used for stable releases. The `dev` branch is used for next releases / prereleases and serves as the main branch for development. Shabad OS follows a _fork and pull model_. Developers should fork the `dev` branch to their personal repository. Developers can create branches off this personal `dev` branch and work on them. Branches should be short-lived and should relate to a single issue from the repo. Avoid updating branches with other branches. Sync your personal branch with upstream dev with a rebase before submitting a PR.

> Keep your personal branches separate from each other. Sync your personal branch with upstream `dev` using rebase.

````
# Replace {repo} with the repo name
git remote add upstream https://github.com/ShabadOS/{repo}.git

# Make sure that you are on your personal branch before syncing
git checkout your-personal-branch 

# Sync your personal branch with upstream dev
git fetch upstream
git rebase upstream/dev
````

Even if you have push rights on the `ShabadOS/{repo}` repository, you should create a personal fork. This keeps the main repository clean and your personal workflow out of sight.

Branches should be named after the issue they are resolving in the format of `issue-<issue_number>(-<hyphenated_description>)` (e.g. `issue-128` for quick fixes or `issue-128-fix-readme-typos` for preferred readability). If there is no issue related to the work being done, then create an issue for tracking purposes.

See the following GitHub docs for additional guidance:

* [Overview of collaborative development models](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-collaborative-development-models)
* [Configuring a remote for a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork)
* [Sync a fork of a repository to keep it up-to-date with the upstream repository](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)

### Pull Requests

To enable quick code reviews, create one pull request per issue. Avoid resolving multiple issues in one PR unless they share a root cause. Be sure to follow the [Coding Guidelines](#coding-guidelines) and keep code changes as small as possible. Avoid pure formatting changes to code that has not been modified otherwise. Pull requests should contain tests whenever possible. The pull requests summary should include changes, tests done, visual before and after, time taken to resolve, and linked issues whenever possible.

## Coding Guidelines

We use spaces, not tabs.

### Names

* Use PascalCase for `type` names
* Use PascalCase for `enum` values
* Use camelCase for `function` and `method` names
* Use camelCase for `property` names and `local variables`
* Use UPPER_SNAKE_CASE for `true constants` (hardcoded string or env variable)
* Use whole words in names when possible

### Comments

Use [JSDoc](https://jsdoc.app/index.html) style comments for `functions`, `interfaces`, `enums`, and `classes`

### Style

Our style guide is very similar to [Airbnb's Javascript Style Guide](https://github.com/airbnb/javascript), apart from a few minor modifications. Notably, spaces should be included inside parentheses and brackets.

### Linting

Many of our repos contain an [ESLint](https://eslint.org/) configuration file. You can run ESLint on any file or directory by running `npx eslint yourfile.js` in a terminal or command prompt.

It is recommended to [integrate ESLint](https://eslint.org/docs/user-guide/integrations) with your editor so you can receive linter suggestions as you type. We recommend [VSCode's ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).

In addition to linting, code will automatically be checked by GitHub Actions for style.

### Commit Messages

Our git commit messages consist of three sections separated by blank lines in the following format:

````
<type>(<scope>): <subject>

<body>

<footer>
````

* Type and subject is mandatory. Scope is optionally added in parentheses. See our [commit history](https://github.com/ShabadOS/{repo}/commits/dev) for examples.
* Use the footer to reference breaking changes and github issues, e.g. `Close #128` or `Related #128`. We use this for automating builds and tracking issues.

#### Type

A majority of our commits tend to be one of the following:

- *feat*: Changes that introduce a new feature or enhancement; Always an addition or improvement.
- *fix*: Changes related to unexpected behavior; Usually bug related, but also for correcting typos/content.
- *perf*: Changes that improve performance.
- *refactor*: Changes that don't alter behavior, don't add features/enhancements, don't affect performance, and don't change anything for the user.

NOTE: Typos are always mistakes, and therefore type *fix*. Additions/enhancements to content are type *feat*.

We have some target level types:

- *build*: Changes to our build system or external dependencies (e.g. with scopes: gulp, broccoli, npm)
- *ci*: Changes to our CI configuration files and scripts (e.g. with scopes: Circle, BrowserStack, SauceLabs)
- *docs*: Changes to our documentation
- *test*: Changes to our tests; Adding missing tests or correcting existing tests

And, the last type:

- *style*: Changes to code that are superficial and do not affect anything in a meaningful way (e.g. white-space, formatting,  missing semi-colons)

#### Scope

Scopes are defined per repo to help a person reading the changelog. Scopes can be empty for broad changes involving `style`, `test`, and `refactor` (e.g. style: add missing semicolons) and for `docs` changes (e.g. docs: fix typo in tutorial).

#### Subject

We begin our subjects in lowercase and remove any trailing punctuation (e.g. period or exclamation mark).

The subject line must be no more than 72 characters. If you're unable to succinctly summarize what you've done, then perhaps too many changes are being committed at once. Aim for smaller commits which can be explained better.

Our subjects are written imperatively. The imperative is the same as if giving a command or instruction. It can be easily tested by substituting the subject for blank in the line "this commit will <blank>". Examples: refactor, update, show, hide, add, remove, allow, prevent, open, close.

#### Body

Code is generally self-explanatory. Not every commit requires a body. Some changes are so simple that no further explanation is necessary. Even complex code should have comments for explanations.

Focus on using the body to explain _why_ you made the changes. Explain how it worked before the change, why it required changing, and why you resolved it the way you did.

If the subject is the command, then the body is the purpose.

#### Footer

If your commit introduces a major breaking change (one that requires a [major version jump](https://semver.org/)), then end the footer with `BREAKING CHANGE`.

If your commit relates to a GitHub issue, then use the footer to link it (e.g. "Related #128"). If your commit would close a GitHub issue when merged, then use the footer to automate it (e.g. "Close #128"). One commit should almost never reference multiple issues, but if need be the commands can be comma-separated (e.g. "Close #128, Close #64, Related #32").

#### Revert

When reverting single commits, modify the header of the commit being reverted by beginning it with `revert: ` and use the body of the commit to reference the SHA hash of the commit being reverted.

*Example commit with SHA abc123*

````
docs: add contributing guidelines
````

*Example of reverting commit with SHA abc123*

````
revert: docs: add contributing guidelines

Reverting commit abc123.
````

## Thank you!

Your contributions to open source, large or small, make great projects like this possible. Thank you for taking the time to participate in this project.
