# 问题
给定一个二叉树，检查它是否是镜像对称的。
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
bool Symmetric(struct TreeNode* rootleft, struct TreeNode* rootright)
{
    if(rootleft == NULL && rootright == NULL)
    {
        return true;
    }
    else if(rootleft == NULL || rootright == NULL)
    {
        return false;
    }
    if(rootleft -> val != rootright -> val)
    {
        return false;
    }
    if(Symmetric(rootleft -> left, rootright -> right) == false || Symmetric(rootleft -> right, rootright -> left) == false)
    {
        return false;
    }
    return true;
}
bool isSymmetric(struct TreeNode* root) {
    if(root == NULL)
    {
        return true;
    }
    return Symmetric(root -> left, root -> right);
}
```
# 心得
如果左右两个根中都为空，说明对称，返回true；如果其中一个为空，另一个不为空，说明不对称，返回false。如果左右两根值不同，不对称，如果左根的右子树和右根的左子树不同或是左根的左子树和右根的右子树不同，都不对称，除去这些情况，可以认为是对称的。然后在主函数程序中，如果根为空，返回true，如果不为空，返回子函数。