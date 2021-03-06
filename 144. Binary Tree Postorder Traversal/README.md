早就在想，后序遍历啥时候来，这下总算姗姗来迟。

后序遍历是三序遍历中最墨迹的一个，因为它是伟大的父母，先让儿子(左子树)走，再让女儿(右子树)走，最后才是自己走。子树当了父母，又是这样做。

这就导致它的迭代有点啰嗦，你想象一下，一个老爹爹，不住的问，儿子走了吗？孙子呢？女儿走了吗？外孙女呢？...几乎要把整个家族数个遍。

所以我的算法思路仍然和之前的 先序、中序差不多，都是弄个堆栈，如果根存在，那么将根入栈，走左子树；问题的关键在于：左子树走到头，回溯的时候，还要顾及右子树，也就是根不能忙着出栈，那问题来了，啥时候出？

答曰：右子树走完的时候。 问题又来了，右子树啥时候走完？我们知道，移到右子树的时候，流程就又回到了最开头。这时候咱们的栈，已经无法起到提醒我们哪些没走的作用，我们缺了个东西。

这个东西我能想到最简单的实现就是一个标记指针。它指向“裸根”，也就是左子树、右子树都走完的根。

- 如果右子树存在，且右子树不是“裸根”（裸根意味着已经走过了），那么才开始迭代右子树。
- 否则，标记“裸根”，记录根值，出栈。与先序、中序的步骤一致。

想到这一点，代码就呼之欲出了。
