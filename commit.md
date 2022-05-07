# 代码提交规范

## 1 commit的内容编写规范

https://zhuanlan.zhihu.com/p/90281637

commit中应包含提交的类型：

    feat: 新功能、新特性
    fix: 修改 bug
    hotfix: 发版后的bug修复
    perf: 更改代码，以提高性能（在不影响代码内部行为的前提下，对程序性能进行优化）
    refactor: 代码重构（重构，在不影响代码内部行为、功能下的代码修改）
    docs: 文档修改
    style: 代码格式修改, 注意不是 css 修改（例如分号修改）
    test: 测试用例新增、修改
    build: 影响项目构建或依赖项修改
    revert: 恢复上一次提交
    ci: 持续集成相关文件修改
    chore: 其他修改（不在上述类型中的修改）
    release: 发布新版本
    workflow: 工作流相关文件修改(github工作流)

commit格式如:

    feat: 审批流查询接口

## 2 pr提交规范

### 2.1 每个pr应该是一个功能或是一个模块

每个pr的提交应该只包含一个功能的修改或者是一个模块的修改，已方便后续问题追溯的过程中可以快速的定位到一个pr对应的代码修改上

### 2.2 合并前准备

#### 2.2.1 合并前rebase目标分支

应该每次在分支提交之前，拉取目标分支代码，再切换回自己的分支再rebase master分支

```git
git checkout master
git pull
git checkout mybranch
git rebase master
```

如果出现冲突则解决冲突后，在继续rebase

```git
解决冲突后
git add .
git rebase --continue
```

#### 2.2.2 合并前压缩commit

每次pr合并的时候应该注意压缩commit，保证主分支的整洁。假设一个pr中包含了3个commit

```git
git rebase -i HEAD~3 # 这里有几个commit就写几
```

rebase之后会两次进入vi编辑器

第一次


然后每次提交pr的时候 rebase一下，把 commit合并成一个 commit，尽量一个提交就做一个功能或者一个功能模块。
在pr提交之前先rebase一下目标分支
如果是咱们在工单系统里面有编号，比如咱们bug有issue-XXXX这种，那就在pr的title里面以“[issue-XXXX]”开头。
