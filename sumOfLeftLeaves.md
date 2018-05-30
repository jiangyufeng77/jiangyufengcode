# 问题
计算给定二叉树的所有左叶子之和。
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
int sumOfLeftLeaves(struct TreeNode* root) {
    int sum = 0;
    if(root == NULL)
    {
        return 0;
    }
    else if((root -> left != NULL) && (root -> left -> left == NULL) && (root -> left -> right == NULL))
    {
        sum = root -> left -> val;
    }
    return sum + sumOfLeftLeaves(root -> left) + sumOfLeftLeaves(root -> right);
}
```
# 心得
设定一个求和值sum，如果根为空，返回0；如果左子树不为空，但是其叶子全为空，说明这是一个左叶子，算入总和中，然后返回下一级的左子树和右子树，进入循环。