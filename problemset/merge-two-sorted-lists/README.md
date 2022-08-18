# 合并两个有序链表

> 难度：简单
>
> https://leetcode.cn/problems/merge-two-sorted-lists/

## 题目

将两个升序链表合并为一个新的 升序 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。

### 示例

#### 示例 1：

![merge-two-sorted-lists](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)

```
输入：l1 = [1,2,4], l2 = [1,3,4]
输出：[1,1,2,3,4,4]
```

#### 示例 2：

```
输入：l1 = [], l2 = []
输出：[]
```

#### 示例 3：

```
输入：l1 = [], l2 = [0]
输出：[0]
```

## 解法

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function (list1, list2) {
  const head = (cur = new ListNode())
  while (list1 && list2) {
    if (list1.val < list2.val) {
      cur.next = new ListNode(list1.val)
      list1 = list1.next
    } else {
      cur.next = new ListNode(list2.val)
      list2 = list2.next
    }
    cur = cur.next
  }
  cur.next = list1 ? list1 : list2

  return head.next
}
```