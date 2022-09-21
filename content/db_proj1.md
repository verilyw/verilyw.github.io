+++
title = "Prject#1-Buffer Pool"
date = 2022-08-25
[taxonomies]
tags = ["database", "project"]
+++

本次实验前后花了两三天的时间吧。实验难度不高，不过一些细节需要把控好，然后就是多使用`LOG`进行调试。

为了方便记忆和回过头查看，大致写个实验总结。(为遵循cmu的学术规则，总结不会贴代码)

## TASK#1-LRU Replacement Policy

实现四个函数:
  + `Victim(frame_id_t*)`
  + `Pin(frame_id_t)`
  + `Unpin(frame_id_t)`
  + `Size()`

使用`lru`的策略进行替换。我们会维护一个`lru_list`的列表，这里主要是`pin`与`unpin`操作，`pin`操作其实可以简单实现为把当前的元素从表中移除出去(如果存在)，而`unpin`操作把元素加入表中(如果不存在), 如果存在，意味着我们再次访问了它。

## TASK#2 - Buffer Pool Manager Instance

这里最好理清楚buffer pool中每个item的一个状态。总的来说，可以用三个状态表示`Free`, `Pin`， `Unpin`。
过程中维护好`meta-data`。

## TASK#3 - Parallel Buffer Pool Manager

没啥可说的，按照提示就能搞定，注意在`new page`的时候使用什么调度。
