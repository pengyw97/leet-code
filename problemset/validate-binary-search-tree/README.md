# 验证二叉搜索树

> 难度：中等
>
> https://leetcode.cn/problems/validate-binary-search-tree

## 题目

给你一个二叉树的根节点`root`，判断其是否是一个有效的二叉搜索树。

**有效**二叉搜索树定义如下：

- 节点的左子树只包含**小于**当前节点的数。
- 节点的右子树只包含**大于**当前节点的数。
- 所有左子树和右子树自身必须也是二叉搜索树。

### 示例

#### 示例 1：

![tree1](https://assets.leetcode.com/uploads/2020/12/01/tree1.jpg)

```
输入：root = [2,1,3]
输出：true
```

#### 示例 2：

![tree2](https://assets.leetcode.com/uploads/2020/12/01/tree2.jpg)

```
输入：root = [5,1,4,null,null,3,6]
输出：false
解释：根节点的值是 5 ，但是右子节点的值是 4 。
```

## 解法

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isValidBST = function (root) {
  const dfs = (root, minVal, maxVal) => {
    if (!root) return true
    if (root.val <= minVal || root.val >= maxVal) {
      return false
    }

    return dfs(root.left, minVal, root.val) && dfs(root.right, root.val, maxVal)
  }

  return dfs(root, -Infinity, Infinity)
}
```
