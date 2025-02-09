## Commitlint rule

> @tsailab commitlint rules like [@commitlint/config-angular](https://github.com/conventional-changelog/commitlint/blob/master/%40commitlint/config-angular/README.md)

```text
<type>(<scope>): <subject> // 必填, 描述主要修改类型和内容。注意冒号后面有空格
<BLANK LINE>
<body> // 描述为什么修改, 做了什么样的修改, 以及开发的思路等等
<BLANK LINE>
<footer> // 放 Breaking Changes 或 Closed Issues
```

## type-enum

| type | Comments | Remark |
| -------- | ------------------------- | ------------------- |
| feat | 新功能（feature）表示在代码库中新增了一个功能 | 这和语义化版本中的 MINOR 相对应 |
| fix | 表示在代码库中修复了一个 bug | 这和语义化版本中的 PATCH 相对应 |
| chore | 当一个提交有其他修改（不在上述类型中的修改） | 一般用在代码合并后发布提交，例如： chore(bot): release version x.x.x  |
| ci | 当一个提交修改了持续集成，示例范围：Travis、Circle、BrowserStack、SauceLabs | -- |
| docs | 当一个提交仅修改了 md 文件或其他阅读性文件时 | -- |
| build | 当一个提交修改了编译相关的内容，发布版本、对项目构建或者依赖的改动 | 即npm、gulp、yarn等文件的修改时，须使用 build 类型 |
| pref | 当一个提交包含优化相关，比如提升性能、优化用户体验时 | -- |
| refactor | 当一个提交既不修复错误也不添加功能的代码更改 | -- |
| revert | 代码回退 | -- |
| refactor | 重构代码，不影响功能和对外提供API 时 | -- |
| style | 当一个提交仅修改了代码格式（如删除空格、换行等）或不影响代码逻辑本身的修改时| -- |

----

## <a name="submit"></a> Submission Guidelines

### <a name="submit-issue"></a> Submitting an Issue

Before you submit an issue, please search the issue tracker, maybe an issue for your problem already exists and the discussion might inform you of workarounds readily available.

We want to fix all the issues as soon as possible, but before fixing a bug we need to reproduce and confirm it. In order to reproduce bugs we will systematically ask you to provide a minimal reproduction scenario using a repository or [Gist](https://gist.github.com/). Having a live, reproducible scenario gives us wealth of important information without going back & forth to you with additional questions like:

- version of Tsai-CLI used (`tsai info`)
- and most importantly - a use-case that fails

Unfortunately, we are not able to investigate / fix bugs without a minimal reproduction, so if we don't hear back from you we are going to close an issue that doesn't have enough info to be reproduced.

You can file new issues by filling out our [new issue form](https://github.com/tsai-plat/tsai-cli/issues/new).

### <a name="submit-pr"></a> Submitting a Pull Request (PR)

Before you submit your Pull Request (PR) consider the following guidelines:

1. Search [GitHub](https://github.com/tsai-plat/tsai-cli/pulls) for an open or closed PR that relates to your submission. You don't want to duplicate effort.
1. Fork the lotolab/tsai-cli repo.
1. Get a gpg key to sign your commits, see [help](https://help.github.com/articles/about-gpg/).
1. Create your patch, **including appropriate test cases**.
1. Commit your changes using a descriptive commit message

   ```shell
   git commit -am "<message>"
   ```

   Note: the optional commit `-a` command line option will automatically "add" and "rm" edited files.

1. Push your branch to GitHub:

   ```shell
   git push origin my-fix-branch
   ```

   Note: you can use -u to set your branch in upstream and just push for the next times.

1. In GitHub, send a pull request to `tsai-plat/tsai-cli:main`.

- If we suggest changes then:

  - Make the required updates.
  - Rebase your branch and force push to your GitHub repository (this will update your Pull Request):

    ```shell
    git rebase main -i
    git push -f
    ```

That's it! Thank you for your contribution!

#### After your pull request is merged

After your pull request is merged, you can safely delete your branch and pull the changes
from the main (upstream) repository:

- Delete the remote branch on GitHub either through the GitHub web UI or your local shell as follows:

  ```shell
  git push origin --delete my-fix-branch
  ```

- Check out the main branch:

  ```shell
  git checkout main -f
  ```

- Delete the local branch:

  ```shell
  git branch -D my-fix-branch
  ```

- Update your main with the latest upstream version:

  ```shell
  git pull --ff upstream main
  ```

  ## <a name="rules"></a> Coding Rules
To ensure consistency throughout the source code, keep these rules in mind as you are working:

* All features or bug fixes **must be tested** by one or more specs (unit-tests).
<!--
// We're working on auto-documentation.
* All public API methods **must be documented**. (Details TBC). -->
* We follow [Google's JavaScript Style Guide][js-style-guide], but wrap all code at
  **100 characters**. An automated formatter is available ( `npm run format` ).

## <a name="commit"></a> Commit Message Guidelines

We have very precise rules over how our git commit messages can be formatted.  This leads to **more
readable messages** that are easy to follow when looking through the **project history**.  But also,
we use the git commit messages to **generate the Tsai change log**.

### Commit Message Format
Each commit message consists of a **header**, a **body** and a **footer**.  The header has a special
format that includes a **type**, a **scope** and a **subject**:

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

The **header** is mandatory and the **scope** of the header is optional.

Any line of the commit message cannot be longer than 100 characters! This allows the message to be easier
to read on GitHub as well as in various git tools.

Footer should contain a [closing reference to an issue](https://help.github.com/articles/closing-issues-via-commit-messages/) if any.

Samples: (even more [samples](https://github.com/tsai-plat/tsai-cli/commits/main))

```
docs(changelog) update change log to beta.5
```
```
fix(tsai-cli) need to depend on latest rxjs and zone.js

The version in our package.json gets copied to the one we publish, and users need the latest of these.
```

### Revert
If the commit reverts a previous commit, it should begin with `revert: `, followed by the header of the reverted commit. In the body it should say: `This reverts commit <hash>.`, where the hash is the SHA of the commit being reverted.

### Type
Must be one of the following:

* **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
* **chore**: Updating tasks etc; no production code change
* **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
* **docs**: Documentation only changes
* **feat**: A new feature
* **fix**: A bug fix
* **perf**: A code change that improves performance
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
* **test**: Adding missing tests or correcting existing tests


### Subject
The subject contains succinct description of the change:

* use the imperative, present tense: "change" not "changed" nor "changes"
* don't capitalize first letter
* no dot (.) at the end

### Body
Just as in the **subject**, use the imperative, present tense: "change" not "changed" nor "changes".
The body should include the motivation for the change and contrast this with previous behavior.

### Footer
The footer should contain any information about **Breaking Changes** and is also the place to
reference GitHub issues that this commit **Closes**.

**Breaking Changes** should start with the word `BREAKING CHANGE:` with a space or two newlines. The rest of the commit message is then used for this.

A detailed explanation can be found in this [document][commit-message-format].

<!-- ## <a name="cla"></a> Signing the CLA

Please sign our Contributor License Agreement (CLA) before sending pull requests. For any code
changes to be accepted, the CLA must be signed. It's a quick process, we promise!

* For individuals we have a [simple click-through form][individual-cla].
* For corporations we'll need you to
  [print, sign and one of scan+email, fax or mail the form][corporate-cla]. -->


<!-- [angular-group]: https://groups.google.com/forum/#!forum/angular -->
<!-- [coc]: https://github.com/angular/code-of-conduct/blob/master/CODE_OF_CONDUCT.md -->
[commit-message-format]: https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#
[corporate-cla]: http://code.google.com/legal/corporate-cla-v1.0.html
[github]: https://github.com/tsai-plat
[discord]: https://discord.gg/lotolab
[individual-cla]: http://code.google.com/legal/individual-cla-v1.0.html
[js-style-guide]: https://google.github.io/styleguide/jsguide.html
[jsfiddle]: http://jsfiddle.net
[plunker]: http://plnkr.co/edit
[runnable]: http://runnable.com
<!-- [stackoverflow]: http://stackoverflow.com/questions/tagged/angular -->

