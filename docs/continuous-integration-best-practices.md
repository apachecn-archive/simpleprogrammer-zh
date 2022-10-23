# 持续集成最佳实践

> 原文:[https://simple programmer . com/continuous-integration-best-practices/](https://simpleprogrammer.com/continuous-integration-best-practices/)

在我之前的[帖子](https://simpleprogrammer.com/2009/12/23/do-you-ci-seeing-u-ciing-continuous-integration/)中，我谈到了为什么你需要开始使用持续集成，需要一个持续集成服务器。在这篇文章中，我将更多地关注当你设置了持续集成服务器时的持续集成最佳实践。

**单元测试**

作为构建的一部分，持续集成服务器需要做的第一件事就是运行并报告单元测试。它并不是一个足够好的质量检查点，无法确保代码编译时没有错误。您的单元测试应该作为每个构建的一部分来执行。每次有人签入代码时，您都想知道单元测试没有中断。除此之外，我还将包括代码覆盖报告。让您的持续集成服务器报告您的代码覆盖率对于您的单元测试的代码覆盖率度量是非常有用的。

**静态分析工具**

实施编码标准和质量标准的最好方法之一是通过使用静态分析工具。根据您使用的语言，有几个选项可供选择。对于 Java，有像 PMD 和 Checkstyle 这样的工具。NET 有 FxCop 和 StyleCop 之类的工具。这里有一个很好的列表,列出了每种语言可用的一些。静态分析工具有两个基本分支，一个检查格式和约定，一个检查不良实践。我强烈建议两者都用。您的 CI 服务器应该在每个构建结束时运行静态分析工具，并且最好跟踪构建中引入的违规的进度。如果一定数量或百分比的代码有违规，一些 CI 服务器允许您实际上使构建失败。对于新的代码库，我强烈推荐这样做。如果你最终有大量的违规行为，这些违规行为就会变成噪音。CI 服务器是让项目中的每个人都能看到这一点的好方法。

**部署**

如果将您的代码部署到任何环境中需要的不仅仅是一个按钮，那么您就错了。我知道这听起来像是一个大胆的声明，但是为什么你需要做更多的事情呢？我一直强调的一点是，构建到达一个环境的唯一方式是从 CI 服务器直接将它推送到那里。基本上，您应该只部署由 CI 服务器构建的构建。当您遵循这一实践时，您可以确保环境中的代码正是您所期望的。从其他地方获取构建是容易出错且有风险的。手动构建既浪费时间，又有风险。您的部署应该是一个简单的按钮，它获取已经在 CI 服务器上构建的位，并将它们部署到所需的环境中。

**通知**

也许 CI 服务器最重要的部分是当构建失败或修复时的通知。如果你犯了这个错误，你将会不断地追赶破坏构建的开发人员，你的努力将会是徒劳的。非常重要的是，当一个构建失败时，这是一件大事，一件真正的大事。有些团队使用闪光灯，有些使用大型平板电视，有些只是电子邮件，但无论你怎么做，都必须有效，不能忽视。我建议在构建失败和修复时至少设置一个电子邮件通知。当有一个坏的构建时，修复这个构建就成了重中之重，这一点非常重要。有助于减少构建中断的一件事情是确保开发人员有办法完成与 CI 服务器完全相同的构建。如果开发人员在签入他们的代码之前可以在本地运行相同的构建，那么就没有什么好的借口来破坏构建。(这也要求构建速度非常快，在我之前的一篇文章中，我提到过[有一个专门的开发工具团队](https://simpleprogrammer.com/2009/12/03/dedicated-developer-tools-teams/)来做优化构建之类的事情。)

**数据库**

我不会在这里详细讨论数据库集成，因为这篇文章的重点是 CI 最佳实践，但是我想强调这一点。如果您的数据库在某种程度上不受版本控制，并且不是用您的源代码构建的，那么拥有复制任何代码构建的能力是没有意义的。基本上，如果您不能将一个同样可复制的数据库版本绑定到源代码，您实际上就不能回滚到特定的时间点。对于一些项目来说，这是重要的，对于其他项目来说，这是不重要的，但对于所有项目来说，这是必须考虑的。无论哪种方式，您都应该最低限度地考虑如何处理与 CI 服务器的数据库集成。在我目前从事的项目中，我帮助采用的一个解决方案是构建一个数据库，其工作方式与源代码构建非常相似，并将数据库更改作为 SQL 更改脚本来应用，这些脚本以一定的顺序应用来构建数据库。