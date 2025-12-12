---
title: "【题解】LeetCode 206. 反转链表"
date: 2025-12-12T19:00:00+08:00
draft: false          # 记得改成 false 才能发布！
tags: ["算法", "链表", "C++"]  # 打标签，方便以后查找
categories: ["刷题日记"]
summary: "这是一道经典的链表题目，详细讲解了双指针法的实现细节。" # 文章摘要
---

## 题目描述
给你单链表的头节点 `head` ，请你反转链表，并返回反转后的链表。

## 思路分析
这道题的核心是使用**双指针**。
1. 定义 `prev` 指针指向 `NULL`。
2. 定义 `curr` 指针指向 `head`。
3. 遍历链表，每次把 `curr` 的 `next` 指向 `prev`。

## 代码实现 (C++)

```cpp
struct ListNode {
    int val;
    ListNode *next;
    ListNode() : val(0), next(nullptr) {}
};

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        while (curr != nullptr) {
            ListNode* nextTemp = curr->next; // 暂存后继节点
            curr->next = prev;               // 修改指向
            prev = curr;                     // prev 后移
            curr = nextTemp;                 // curr 后移
        }
        return prev;
    }
};