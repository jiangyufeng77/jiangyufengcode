# 问题
给定一个二叉搜索树，同时给定最小边界L 和最大边界 R。通过修剪二叉搜索树，使得所有节点的值在[L, R]中 (R>=L) 。你可能需要改变树的根节点，所以结果应当返回修剪好的二叉搜索树的新的根节点。
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
struct TreeNode* trimBST(struct TreeNode* root, int L, int R) {
    if(!root)
        return NULL;
    if(root -> val < L)
        return trimBST(root -> right, L, R);
    if(root -> val > R)
        return trimBST(root -> left, L, R);
    root -> right = trimBST(root -> right, L, R);
    root -> left = trimBST(root -> left, L,R);
    return root;
}
```
# 心得
如果根节点为0，则返回空；如果根节点比下界小，则改变根节点，从右子树开始，反之，则从左子树开始。依次遍历每个节点，并与上下界进行比较，去掉不符合的节点。