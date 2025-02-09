### 主分支 `main`

- main 为主分支，要保护它的稳定性，随时可用来上线。
- 我们不应该直接在 main 分支上直接提交代码，而是从其它分支的合并。

### 开发分支 develop

- develop 为开发分支，一般包含正在开发的所有新特性，用于测试环境部署和测试。
- 我们不应该直接在 develop 分支上直接提交代码，也不应该把未经测试的代码合并进来，应该尽量保持测试环境干净可用。
- 当 develop 太“脏”以至于不能继续测试之后，可以考虑重新从 main 拉取一次。

### 特性分支 feature

- _分支命名_: feature/ 开头的为特性分支，命名规则为 feature/some_amazing_funs-yourname-date。举例来讲，如天宇10月18日要开发一个通讯录改进的功能，可以自建分支为 feature/contacts_advance-ty-1018。
- 一般 feature 分支应仅包含一个特性，上线（合并至 main）部署验证无误后即可删除。记得及时将 feature 分支 push 至远端。
- 如果合并至 develop 或 main 时发现在 fork 此特性分支之后分支已合并了很多其它分支的提交，请先执行 git rebase，这样能提交历史更加整洁。

### 预上线分支 release
- _分支命名_: release/ 开头的为预发布分支，命名规则为 release/date。举例来讲，如果10月18日要准备封一个预上线分支，则命名为 release/1018。
- 上线后即可删除。

### 快速修复分支 hotfix
- _分支命名_: hotfix/ 开头的为修复分支，它的命名规则与 feature 分支类似。
- 一般我们如果发现紧急线上 bug，可以将线上代码临时回滚，从最新的 master 分支建立 hotfix 分支，提交修复代码、测试无误后，合并至 develop 和 main。
- 上线验证无误后，即可将 hotfix 分支删除。
