# 问题
给定两个二叉树，编写一个函数来检验它们是否相同。

如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。

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
bool isSameTree(struct TreeNode* p, struct TreeNode* q) {
    if(p == NULL && q == NULL)
        return true;
    if((p != NULL && q == NULL) || (p == NULL && q !=NULL))
        return false;
    if(p -> val != q ->val)
    {
        return false;
    }
    else 
    {
        return isSameTree(p -> left , q ->left) && isSameTree(p ->right , q -> right);
    }
}
```
# 心得
如果两个树都为空，则两树相同；如果一个树为空，另一个不为空，则不同；两树都不为空的时候，如果节点处的值不同，则不同，否则就相同。
bool型变量的值只有真和假，即true和false。