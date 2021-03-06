如何过渡至 Python 3 
===============================

原文地址： http://www.aaronsw.com/weblog/python3

译者： `yudun1989 <http://www.douban.com/people/yudun1989/>`_

作为一个普通的 Python 开发者，不免会碰到 Python 2 到 3 转换不成功的问题。我经常会得到一些请求说要让我写的库能够在 Python 3 中运行，但是对于如何升级这个问题，在我尝试了各种各样解决冲突的建议之后，并没有发现有多少个可行的方案。

确实，当你看到新的 3.x 匆匆发布，却没有多少人来使用，难免会去猜测 Python 是否会在这次艰难的转型中倒下。那么我们应该如何来帮助它越过这道坎？

我似乎看到很多关于 Python 3 彻底的，未来的，崭新的版本特性的讨论，但我们却忽视了升级的方法。在 Python 2 时代，我们有非常清楚的方法来应对版本更新。

- 在 Python 2.a 版本中， 加入了 ``from __future__ import new_feature`` 语句，你就可以明确声明你想要使用的新特性来使用新功能。

- 在 Python 2.b 版本中， 默认加入了新功能，你不需要在使用之前去声明 future。

- 在 Python 2.c 版本中，当你在使用旧的方法时，将会产生警告，来通知你改变你的既有代码，或者是停止运行。

- 在 Python 2.d 版本中，它就真的停止工作了。

这种方法可能确实蛮有效，但是我却不清楚为什么在向 Python 3 转换的过程中，却没有什么效果。它可能只是想表达：

- Python 2.x 版本将会支持 ``from __future__ import python3``

将这个加在文件的首部将会声明这是一个 Python 3 文件，编译器将会正确的解析它 (我意识到这样做可能会为 Python 2 和 3 的编译器带来许多繁重的工作，但是坦诚地说，维护一个统一的代码库永远都是件好事)。

如果我想让我基于 Python 2 的程序去使用一些属于 Python 3 的模块，我只需要确认这些模块在头部都有调用 import 。如果我想给我的模块发布一个可以在 Python 3 上运行的新版本，我只需要声明这个程序只在 Python 2.x 或更高版本中运行(使用新的 ``import`` 语句)。如果项目比较大，我甚至可以一次性地将版本升级到 3，留下旧代码，直到一些人来修正这些琐碎。最重要的，我可以升级到 Python 3 而不必等到所有的依赖都满足、直到有一个完整的方案时才来解决。

用户只有知道在不改变既有代码的情况下他们才会升级到 2.x 版本。开发者知道大家最终会升级到 2.x 所以他们放弃对之前版本的支持。但是既然 2.x 的代码在 3 下也兼容，那么他们就会开始编写和发布可以和未来兼容的代码，最终大部分的代码都将会在 Python 3 下工作，用户也会升级到 3 (2.x 将会对一些残余的代码给以警告)。最后我们可以丢掉对 2.x 的支持，然后让所有的代码都能得到更好的兼容。

这不是一个激进的点子，这是 Python 升级既有的方式。除非我们再次这样做，否则我不知道我们如何才能渡过这个艰难的阶段。
