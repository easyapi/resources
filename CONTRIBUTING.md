# 为EasyAPI做贡献

我们很乐意您为贡献EasyAPI并帮助它变得比现在更好！作为贡献者，以下是我们希望您遵循的准则：

 - [行为准则](#coc)
 - [建议和BUG](#issue)
 - [功能请求](#feature)
 - [提交指南](#submit)
 - [编码规则](#rules)
 - [提交消息指南](#commit)
 - [版权申明](#cla)

## <a name="coc"></a> 行为准则
帮助我们保持EasyAPI的开放性和包容性。请阅读并遵守我们的[贡献者行为准则][coc]。

## <a name="issue"></a> 发现了一个Bug？
如果您在源代码中发现错误，可以通过向我们的GitHub提交问题来帮助我们 。更好的方案是，您可以直接提交带有修复的Pull Request。

## <a name="feature"></a> 功能建议
您可以通过向我们的GitHub提交新功能*请求*。如果您想要实施新功能，请先提交有关您工作的提案的问题，以确保我们可以使用它。请考虑它是什么样的变化：

* 对于主要功能，首先新建一个问题并概述您的提案，以便进行讨论。这也将使我们能够更好地协调我们的工作，防止重复工作，并帮助您制定变更，以便成功地将其纳入项目。
* **小功能**可以开发并直接作为[Pull Request提交](#submit-pr)。

## <a name="submit"></a> 提交指南

### <a name="submit-issue"></a> 提交问题

在您提交问题之前，请搜索问题跟踪器，可能是您的问题已存在的问题，讨论可能会告知您可以随时使用的解决方法。

我们希望尽快解决所有问题，但在修复错误之前，我们需要重现并确认它。为了重现错误，我们将系统地要求您提供最小的复制。具有最小可重现性的场景为我们提供了大量重要信息，而无需向您回复并提出其他问题。

最小的再现允许我们快速确认错误（或指出编码问题），并确认我们正在解决正确的问题。

我们将坚持最小的复制方案，以节省维护者的时间，并最终能够修复更多​​的错误。有趣的是，根据我们的经验，用户在准备最小复制时经常会发现编码问题。我们知道，有时可能很难从更大的代码库中提取必要的代码，但我们确实需要先解决问题，然后再修复它。

不幸的是，我们无法在没有最小再现的情况下调查/修复错误，因此如果我们没有收到您的回复，我们将关闭一个没有足够信息可以复制的问题。

您可以通过从我们的新问题模板中选择并填写问题模板来提交新问题。


### <a name="submit-pr"></a> 提交拉取请求（PR）
在提交Pull Request（PR）之前，请考虑以下准则：

1. 在GitHub上搜索与您的提交相关的开放或已关闭的公关。你不想重复努力。

2. 确保问题描述了您正在修复的问题，或者记录您要添加的功能的设计。预先讨论设计有助于确保我们准备接受您的工作。

3. Fork相关代码.
4. 在新的Git分支中进行更改

     ```shell
     git checkout -b my-fix-branch master
     ```

5. 创建补丁。
6. 遵循我们的[编码规则](#rules)。 
7. 使用遵循我们的[提交消息约定](#commit)的描述性提交消息提交您的更改 。必须遵守这些约定，因为这些消息会自动生成发行说明。

     ```shell
     git commit -a
     ```
    注意：可选的commit `-a`命令行选项将自动 "add" 和 "rm" 编辑的文件。

8. 将您的分支推送到GitHub：

    ```shell
    git push origin my-fix-branch
    ```

9. 在GitHub中，发送一个拉取请求。

感谢您的贡献！


#### 合并拉取请求后

合并拉取请求后，您可以安全地删除分支并从主仓库中提取更改：

* 通过GitHub Web UI或本地shell删除GitHub上的远程分支，如下所示：

    ```shell
    git push origin --delete my-fix-branch
    ```

* 查看主分支：

    ```shell
    git checkout master -f
    ```

* 删除本地分支：

    ```shell
    git branch -D my-fix-branch
    ```

* 使用最新的仓库版本更新您的仓库：

    ```shell
    git pull --ff upstream master
    ```

## <a name="rules"></a> 编码规则
为确保整个源代码的一致性，请在工作时牢记这些规则：
* 所有功能或错误修复必须通过一个或多个规范（单元测试）进行测试。
* 必须记录所有公共API方法。（详情TBC）
* 我们遵循[Google的JavaScript样式指南][js-style-guide]，但所有代码都包含 100个字符。可以使用自动格式化程序，请参阅 DEVELOPER.md。

## <a name="commit"></a> 提交消息指南

我们对如何格式化git提交消息有非常精确的规则。这样可以查看更易读的消息，这些消息在查看项目历史记录时很容易理解。

### 提交消息格式
详情和标题间隔一个空行。大部分 commit 应该保持目的单一，不需要详情部分。对于原因不是显而易见，或者原理需要解释的 commit，可以在这个部分说明。如果只是一个简单的句子，可以使用与标题描述部分相同的格式。如果超过一行，请按照常规的段落格式，包括句首字母大写，正确使用标点等。详情可以有多行、多段，每行不超过 72 个字符，行尾不要有空格，段落之间用空行隔开。

示例：

```
docs(changelog): 更新版本beta.5
```
```
fix(release): need to depend on latest rxjs and zone.js

The version in our package.json gets copied to the one we publish, and users need the latest of these.
```

### 还原
如果提交恢复了先前的提交，则应该首先提交，`revert: ` 然后是恢复的提交的标头。在正文中它应该说：`This reverts commit <hash>.`，其中哈希是被还原的提交的SHA。


### 类型
必须是以下之一：

* **build**: 和构建流程、持续集成等有关的改动
* **docs**: 对文档的改进，包括对外文档和代码注释
* **feat**: feature - 所有实现新功能、新行为的 commit 都属这个类型
* **fix**: 修正缺陷的 commit
* **perf**: 代码性能改进
* **refactor**: 不改变行为的对代码结构的改进
* **style**: 对代码风格的修正（仅限缩进、空行一类的简单改动，对结构有影响的用 refactor）
* **cosm**: cosmetic - 不改变行为的对界面的纯视觉上的改动
* **chore**: 日常维护性改动
* **test**: 与测试有关的改动


## <a name="cla"></a> 版权申明

EasyAPI产品上线后，为了满足广大开发者用户的使用，特推出前端开源产品，为了充分发挥我们的用户群体优势，希望大家共同完善EasyAPI产品，EasyAPI自始至终版权均为EasyAPI运营公司所有，EasyAPI给予开发者投入回报包括收入分成，免费试用特权，旅游奖励。

<hr>


[angular-group]: https://groups.google.com/forum/#!forum/angular
[coc]: https://github.com/angular/code-of-conduct/blob/master/CODE_OF_CONDUCT.md
[commit-message-format]: https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#
[corporate-cla]: http://code.google.com/legal/corporate-cla-v1.0.html
[dev-doc]: https://github.com/angular/angular/blob/master/docs/DEVELOPER.md
[github]: https://github.com/angular/angular
[gitter]: https://gitter.im/angular/angular
[individual-cla]: http://code.google.com/legal/individual-cla-v1.0.html
[js-style-guide]: https://google.github.io/styleguide/jsguide.html
[jsfiddle]: http://jsfiddle.net
[plunker]: http://plnkr.co/edit
[runnable]: http://runnable.com
[stackoverflow]: http://stackoverflow.com/questions/tagged/angular
