# 你看见你在抽烟吗？连续累计

> 原文:[https://simple programmer . com/do-you-ci-seeing-u-ciing-continuous-integration/](https://simpleprogrammer.com/do-you-ci-seeing-u-ciing-continuous-integration/)

### 你的团队正在使用某种形式的持续集成吗？

如果没有，为什么没有？

持续集成是良好开发过程的标志之一。我已经在我参与的每个项目中持续集成了很多年。我通常是架设持续集成服务器的人，因为我认为它是“必须的”

**什么是持续集成？**

如果你不知道持续集成是什么，它基本上是一个构建服务器，每当有人签入一个变更时，它就构建软件。如果你熟悉术语*每夜构建*，或者*每周构建*，持续集成是*每次签入构建*。

我有一个夜间构建，为什么我需要一个持续集成构建？

我将从这里开始，并假设您理解每夜构建的价值。最大的问题和原因就是一个简单的词:

# 反馈

你的反馈回路越紧密，你的转向就越准确。想象一下，如果在汽车中转动方向盘，车轮实际转动之间会有 2 秒钟的延迟。或者当你看后视镜时，你实际上看到了两秒钟前的影像。这会影响你的驾驶能力吗？我当然希望如此。

驱动隐喻是夜间构建与连续构建的对比。当您每晚都获得关于您的构建是否崩溃的信息时，您获得信息已经太晚了。当你的方向正确的时候，你已经失去了宝贵的时间，你的一些开发人员可能已经进入了一条沟。一旦有人犯了不好的代码，我想知道，我想让他们知道。构建保持中断的每一秒钟都是其他开发人员无法获得最新代码并构建系统或检查他们的更改没有中断构建的时间。

我如何获得这种持续集成的好处？

有很多选择，实际上大多数都很好。

为了。NET 世界中，Visual Studio Team Systems 实际上集成了一个持续集成服务器，现在称为 [Team Foundation Build](http://msdn.microsoft.com/en-us/library/ms364045(VS.80).aspx) 。

还有经典的[巡航控制。NET](http://confluence.public.thoughtworks.org/display/CCNET/Welcome+to+CruiseControl.NET) ，Java 也有，但是有点发霉[巡航](http://sourceforge.net/projects/ccnet/)。

对于 Java 或者。我现在更喜欢 Hudson，尽管它可能更适合 Java。

我听说过关于[lunt build](http://luntbuild.javaforge.com/)和[team city](http://www.jetbrains.com/teamcity/index.html)的好消息。

好的持续集成系统是由什么组成的？

在我的下一篇文章中，我将从你应该拥有什么和什么是重要的角度来讲述如何设置你的服务器。我将讨论单元测试支持、代码覆盖率以及您应该使用 CI 服务器做的所有其他好事情。