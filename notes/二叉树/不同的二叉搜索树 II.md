# 不同的二叉搜索树 II

## 题目链接

[95. 不同的二叉搜索树 II](https://leetcode-cn.com/problems/unique-binary-search-trees-ii/)

![](../../pics/不同的二叉搜索树%20II.png)

## 思路分析

函数签名如下：

```java
public List<TreeNode> generateTrees
```

与题 [不同的二叉搜索树](https://github.com/CheneyKwok/algorithm-notes/blob/main/notes/二叉树/不同的二叉搜索树.md) 思路相同，但是要枚举出每一个 BST。

## 代码实现

```java
class Solution{

    public List<TreeNode> generateTrees(int n){
        return generate(1, n);
    }

    List<TreeNode> generate(int lo, int hi){
        List<TreeNode> res = new ArrayList<>();
        
        if(lo > hi){
            res.add(null);
            return res;
        }

        for(int i=lo; i<=hi; i++){
            List<TreeNode> left = generate(lo, i - 1);
            List<TreeNode> right = generate(i + 1, hi);
            // 枚举所有 BST
            for(TreeNode leftNode : left){
                for(TreeNode rightNode : right){
                    TreeNode root = new TreeNode(i);
                    root.right = rightNode;
                    root.left = leftNode;
                    res.add(root);
                }
            }
        }

        return res;
        
    }
}
```
