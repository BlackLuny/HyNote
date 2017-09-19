<!--toc-->

- [普通树的实现（多叉树的实现）](#普通树的实现多叉树的实现)
	- [兄弟结点](#兄弟结点)
	- [森林](#森林)
	- [子节点指针数组](#子节点指针数组)
		- [缺点](#缺点)
		- [优化](#优化)
	- [左兄弟右儿子](#左兄弟右儿子)
		- [森林的表示](#森林的表示)
	- [parent pointer 父指针](#parent-pointer-父指针)

<!-- tocstop -->
# 普通树的实现（多叉树的实现）

## 兄弟结点
父节点相同的节点

## 森林
树的集合

## 子节点指针数组
类似二叉树指针的实现形式，这里使用数组存放子节点的指针
```{cpp}
Node{
  Elem e;
  int childSize;
  Linked-List children's Pointers;
}
```

### 缺点
控制指针太多,如图:
![1]

### 优化
根据上图，直接把子节点 合并上 父节点中的子节点点指针列表(见左兄弟右儿子)

## 左兄弟右儿子
这里实际上本质还是二叉树，但是可以用二叉树来表示普通树
定义树的，左分支的节点为第一个子节点，定义右分支的节点为兄弟节点。

### 森林的表示
实际上，不同的树，也可以看成是兄弟节点（虚构一个共同的根节点）
那么 左兄弟右儿子 也可以描述一个森林

## parent pointer 父指针
建立一个父指针数组，和 值数组
优点：找祖先容易

应用：并查集(不关心父亲是谁，只关心是否是一个等价类)
优化：
1. 路径压缩（find 的时候，把父亲节点设置成根）
2. 加权合并（合并两棵树的时候，把节点少多的树根 设置成 合并后的树的根 ）

[1]:assets/GeneralTree-6921d.png