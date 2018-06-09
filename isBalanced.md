# 问题
给定一个二叉树，确定它是否是高度平衡的。

对于这个问题，一个高度平衡的二叉树被定义为：

一棵二叉树，其中每个节点的两个子树的深度不会相差超过1。
# 程序
```C
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
int heightBalanced(struct TreeNode * root, bool *result) {
    if(!root) 
    {
        return 0;
    }
    int left = heightBalanced(root -> left, result);
    int right = heightBalanced(root -> right, result);
    if(left - right > 1 || right - left > 1) 
    {
        *result = false;
    }
    return left > right ? left + 1 : right + 1;
}
bool isBalanced(struct TreeNode* root) {
    bool res = true;
    heightBalanced(root, &res);
    return res;
}
```
# 心得
先在一个程序中说明如果左子树的深度比右子树的深度大于1，或是右子树的深度比左子树的深度大于1，说明不是高度平衡二叉树，返回false，如果左子树比右子树大，则左子树加一，否则右子树加一。在另一个程序中引用上一个程序，得到true的结果。