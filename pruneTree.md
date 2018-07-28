# 问题
给定二叉树根结点 root ，此外树的每个结点的值要么是 0，要么是 1。

返回移除了所有不包含 1 的子树的原二叉树。

( 节点 X 的子树为 X 本身，以及所有 X 的后代。)
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
struct TreeNode* pruneTree(struct TreeNode* root) {
    if(root==NULL)
        return NULL;
    root -> left = pruneTree(root -> left);
    root -> right = pruneTree(root -> right);
    if(root -> val == 0 && root -> left == NULL && root -> right == NULL)
    {
        return NULL;
    }
    return root;
}
```
# 心得
采用递归的思想。如果根为空，则返回空。如果根为0，且没有左右子树，也返回空。如果节点的值不为空，则将左右节点调用递归函数的值赋值给其左右节点，返回根。