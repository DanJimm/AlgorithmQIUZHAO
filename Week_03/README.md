学习笔记
第三周的内容比较多，而且都不太好理解，特别是回溯，迭代等解题思路。但是像电话号码组合，N皇后等题目，第一次做的时候很蒙蔽，但是做了一次之后，发现，其实这个也是可以套用模板来解决，生成括号和爬楼梯问题的模板可以解决简单的回溯问题。鉴于回溯问题，N皇后我自己解了很久，自己的体会就是回溯的边界值判断和处理上一层的数据这两点，一定要在写代码之前想的很清楚，自顶向下的代码思想，先理清思路和代码框架，再完善代码。
关于DFS和BFS，我个人的理解是，DFS就是递归的思想。不不停的下探，找到目标数组或者矩阵的最底层，然后在每一层的函数中按照题目要求处理。其中分两种代码框架，递归方法，或者是用一个栈维护待处理的node，用栈维护的时候要特别注意node的入栈和出栈的顺序。BFS的话是每次都处理所有上一层节点相关的节点，处理完之后更新待处理的节点列表，印象比较深的一个题是基因变换和单词接龙，基因变换的题目到时很快的解决了，但是单词接龙耗费了很多时间，原因就是单词接龙的字库特长，每次处理当前节点的关联节点的时候，耗时都是O(n)的，这样的耗时在N很大的时候就是不可接受的了。因此以后遇到这类题目的时候，要特别注意，如果性能很差，尽量看看能否优化这个O(N)的时间复杂度。
关于超哥的思考题：使用二分查找，寻找一个半有序数组 [4, 5, 6, 7, 0, 1, 2] 中间无序的地方。二分查找的思路是初始左右边界为数组的最左和最右，然后得到mid，由于这个数组是半有序的，因此我们只需要判断mid和left的大小，如果mid<left那么无序的地方就在mid和left中间，然后继续向中间夹逼mid的下标即可。
