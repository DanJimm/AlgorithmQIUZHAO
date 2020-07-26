学习笔记
week2
本周刷的最多的题就是二叉树相关的内容，牢记二叉树的三种遍历形式，把递归解法的模板背下来，达到提笔直接就能写下模板的程度。
def dfs:-前序遍历
    if root:
        res.append(root.val)
        dfs(root.left)
        dfs(root.right)

def dfs:-中序遍历
    if root:
        dfs(root.left)
        res.append(root.val)
        dfs(root.right)

def dfs:--后序遍历
    if root:
        dfs(root.left)
        dfs(root.right)
        res.append(root.val)

比较难的是迭代的解法，其中前序和后序遍历还是比较容易理解的，难点是中序遍历。
迭代的思路就是用一个栈保存待处理的节点，因此关键点就是节点入栈顺序，以及什么时候处理节点值
前序：
node =[root]
while node：
    cur_node = node.pop()
    result.append(cur_node)
    node.append(cur_node.left)
    node.append(cur_node.right)
return result
后序类似就不写了

重点是中序，中序要实现的是 左-中-右
但是栈的特点是先进后出，如果要实现这个顺序就需要入栈顺序为
右-中-左，这里就有个问题，处理树的遍历，首先入栈的是根节点，因此这里需要做一下特殊的处理，入栈顺序变更为，先入栈根节点，然后入栈左子树，这时候进行出栈操作，并且在出栈的时候记录节点的值。

伪代码如下：
stack , cur,res = [],root,[]
while stack or cur:
    while cur:
        stack.append(cur)
        cur = cur.left
    tmp = stack.pop()
    res.append(tmp.val)
    cur = tmp.right
return res

感觉这周理解的不是很到位的是堆，定义是比较清楚了，但是堆的使用场景不是很熟练，还不能看到一个题就能反映出来是用堆来解决。
比较典型的是前k个高频元素这样的题，可以很快反映过来是用堆解决。但是丑数这题就想不到可以用堆来解决，而且是用堆来保存待处理的丑数列表，我个人的理解是利用了堆的唯一性，和有序性，待处理的数是一个有序且不重复的序列，利用堆的定义正好可以保证堆中的数都是还没有处理的，且题目要求的是第k个数，堆的有序性，正好可以满足、

图论相关的题目做的比较少，唯一刷了几遍的题目是岛屿数量这个题，这个题很形象的利用图的定义，映像比较深刻，过一段时间再回来刷这个题和相关的其他题目。