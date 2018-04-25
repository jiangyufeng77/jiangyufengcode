# 问题
给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。

说明: 叶子节点是指没有子节点的节点。
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
bool hasPathSum(struct TreeNode* root, int sum) {
    if(root == NULL)
        return false;
    if(root -> left == NULL && root -> right == NULL && root -> val == sum)
        return true;
    return(hasPathSum(root -> left,sum - root ->val) || hasPathSum(root -> right, sum - root -> val));
}
```
# 心得
如果根节点为空，则false；如果左右子树均为空，但根节点和sum数值相同，则true；遍历左右子树，看左子树或右子树相加的值是否等于sum和根节点数值相减。