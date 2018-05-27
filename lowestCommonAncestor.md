# 问题
给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。

百度百科中最近公共祖先的定义为： “对于有根树T的两个结点u、v，最近公共祖先表示一个结点x，满足x是u、v的祖先且x的深度尽可能大。”（一个节点也可以是它自己的祖先）

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
struct TreeNode* lowestCommonAncestor(struct TreeNode* root, struct TreeNode* p, struct TreeNode* q) {
    if(p -> val == root -> val) 
    {
        return p;
    }
    else if(q -> val == root -> val) 
    {
        return q;
    }
    else if(p -> val > root -> val && q -> val > root -> val) 
    {
        return lowestCommonAncestor(root -> right,p,q);
    }
    else if(p -> val < root -> val && q -> val < root -> val) 
    {
        return lowestCommonAncestor(root -> left,p,q);
    }
    else 
    {
        return root;
    }
}
```
# 心得
二叉树的特点是若它的左子树不空，则左子树上所有结点的值均小于它的根结点的值；若它的右子树不空，则右子树上所有结点的值均大于它的根结点的值。因为根据定义最近公共祖先节点可以为指定节点自身，所以当p或q有一个的值与根的值相同时返回p或q。因为当p和q的值都大于（小于）根的值，根据定义，大于的时候，返回右子树，小于的时候，返回左子树。如果一大一小，即可返回根了。