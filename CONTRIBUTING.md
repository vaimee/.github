# Contributing to a VAIMEE open source project

VAIMEE believes in the community of talented open source developers. Any contribution is welcomed, whether it be a bug fix, a new feature, a new tool, or a new way of thinking. This document provides a short how-to and a set of guidelines to follow when contributing to one of our open source products.

## How to contribute with code
We use github to host code, track issues, feature requests, and accept pull requests. Once we reach the `1.0.0` all code changes must happen using [Github Flow](https://docs.github.com/en/get-started/quickstart/github-flow), so **all** code changes happen through pull requests. Before `1.0.0` we might tolerate direct commits to `main` but we strongly encourage the use of pull requests to allow for a team wide code review.
We actively welcome your pull requests:

1. Fork the repo and create your branch from `main`.
2. If you've added code, add tests to validate it.
3. If you've changed APIs, update the documentation if any.
4. Ensure the test suite passes.
5. Make sure your code lints.
6. Issue that pull request!

If your PR fixes a bug or an issue, make sure to mention the issue number in the PR title, PR body, or commit message. If the issue does not exist, please take some time to create it.

### Commit messages

We use [Conventional Commit Messages](https://www.conventionalcommits.org/en/v1.0.0/#specification) to ensure that all commits are well-formed. Additionally to the standard commit types, we use the following custom commit types:
- `docs`: for commits that update the documentation.
- `test`: for commits that update the test suite.
- `style`: for commits that update the style.
- `refactor`: for commits meant to be refactoring.
- `chore`: for commits that modify external scripts or `packages.json` dependencies.

Examples:
```
docs: define a new readme structure
```
```
fix: add the local identifier to anonymous td during retrieve and list operations
    
Fixes #3
```

In case of a mono-repo with multiple packages or components, we strongly encourage to specify the package/component name in the commit message as scope. For example give this folder structure:
```
packages
├── core
│   ├── package.json
│   └── src
│       ├── index.ts
│       └── core.ts
└── utils
    ├── package.json
    └── src
        ├── index.ts
        └── utils.ts
```

Supposing you introduce a new function in `core.ts` you should write the following commit message:
```
feat(core): add the new function
```
Expanding scope is also encouraged, for example:
```
feat(core/utils): add the new function
```


## How to contribute with issues
**Great Bug Reports** tend to have:

- A quick summary and/or background
- Steps to reproduce
  - Be specific!
  - Give sample code if you can. [This example of issue report](http://stackoverflow.com/q/12488905/180626) includes sample code that *anyone* with a base R setup can run to reproduce what I was seeing
- What you expected would happen
- What actually happens
- Notes (possibly including why you think this might be happening or stuff you tried that didn't work)

If the repository your are contributing to contains a Issue Template, please follow it. If not, please follow the guidelines above. 

### Discussing on the issue tracker

Be polite and assume that not everyone is an expert. Take time to write a proper introduction if you are taking for granted some complex concepts. If you are claiming something to be true please provide proper reference and background. Links to commit history or code snippets are always recommended.

## How to contribute with a PR

Follow the [Github Flow](https://docs.github.com/en/get-started/quickstart/github-flow) and make sure that your PR is well formed. If you are not sure, please ask for help. If you are contributing to a repository that contains a PR template, please follow it. If not, please follow the guidelines in this document and in the specific project's CONTRIBUTING.md. 

### PR review
When reviewing a PR please keep in mind [How to make technical choices](#how-to-make-technical-choices) section. Our general policy is that a PR can be merged after two core maintainers approve it, but specific projects can override this rule. Further reviews can be asked for increase the confidence or if the committer wants a specific opinion. If there is a tie in the voting, the PR will be merged or closed after the tie breaker vote from the CTO. Decision can be always contested in the PR discussions. 




## But it works on my computer!

We use [Docker](https://www.docker.com/) to ensure that all developers work in the same environment. We strongly encourage you to use it as well. If you are not familiar with Docker, please take some time to learn it. It will save you a lot of time in the long run. We usually don't tolerate the "it works on my computer" excuse. If you are not able to run the test suite locally, please use the CI/CD pipeline to validate your changes. On the other hand, we are always happy to help you to correctly configure your development environment and solve any issue you might have.

Sometimes Docker is not sufficient to ensure that all developers work in the same environment. For example, if you are developing a web application, you might need to install a specific version of Node.js. Therefore, you have to keep in mind that you are working as part of a team and that your code will be executed in a different environment. If you continuously keep shortcuts and workarounds and tangle your code with your environment configuration you are not helping your team and you are not helping us to build better software. If you are aware of a workaround or a shortcut, please talk with your team members before introducing it in the codebase. If you are not sure, please open an issue and/or ask for help.

## Code guidelines and patterns

This section contains a set of guidelines and patterns that we follow when writing code. We strongly encourage you to follow them as well. Usually, most of the stylistic choices are validated by the linter, so you should not worry about them as long as you follow the linter suggestions. Not following the linter suggestions will result in broken CI/CD validation and it can lead to the rejection of your PR. Project specific guidelines and patterns are usually documented in the project's CONTRIBUTING.md, please refer to it for more information. 

### Consistency consistency consistency consistency

We value consistency over everything else. If you are working on a project that already has a codebase, please follow the existing patterns and conventions. If you are working on a new project, please take some time to define a set of conventions and patterns and stick to them. It is a good practice to describe your patterns in the CONTRIBUTING.md file of your project.

Of course not everyone's is perfect and we might bake into our solution some inconsistency. If you spot one, please open an issue and/or a PR to fix it.

> [!NOTE]: TIP
> When creating a new project and you are not sure about the conventions and patterns to follow, please take a look to our previously made projects. If you can't find any project that is similar to what you are building, I am sure that you can find some inspiration on the open source projects hosted in Github. 

### Naming

As developers we know how the naming of variables, functions, classes, and files is important. We also know how hard it is to find the right name. We don't have a silver bullet for this problem, but we can give you some guidelines to follow. First of all, please use English. If you are not a native English speaker, do your best to translate your thoughts using some of free online translators. Try to use evocative names and avoid abbreviations, you have plenty of space to write your code (unless you are working on highly constraint environment). If you are not sure about a name, your team is there to help you. 

> [!WARNING]: TIP
> Per [our consistency rule](#consistency-consistency-consistency-consistency), please follow the naming conventions already used in the project. 

### DRY - Don't Repeat Yourself

We value DRY code. If you find yourself copy-pasting code, please stop and think about it. If you are copy-pasting code because you are lazy, please stop and think about it. If you are copy-pasting code because you are not sure how to refactor it, please stop and think about it. If you are copy-pasting code because you are not sure how to refactor it, please ask for help. 

### How to make technical choices

During your time as our developer you will face technical challenges that does not have a clear answer. In these cases, we encourage you to provide the team all the information needed to understand the different options and to make informed decisions. In general, we value implementation that:
- simplify the codebase and or reduce the complexity (e.g., reduce the number of dependencies)
- make the code more readable/maintainable
- make the code more performant

Note that the list above is not ordered by priority and sometimes we might choose a solution that does not follow any of the points above if it is the best solution for the problem at hand. If possible the discussion should be kept in the issue tracker and openly available to everyone. We require any participant in the dicussion to be polite and keep an objective attitude, subjective preferences should be noted and discussed but they should not be the main driver of the decision.

