# 问题
给定一个二叉树，找出其最大深度。
二叉树的深度为根节点到最远叶节点的最长路径上的节点数。

# 程序

```C
int maxDepth(struct TreeNode* root) {
    if(root==NULL)
        return 0;
    else{
          int left= maxDepth(root->left);
          int right = maxDepth(root->right);
          if(left > right)
              return left + 1;
          else
              return right + 1 ;
    }
}
```
# 心得
如果二叉树为空，则深度为0。如果不为空，则分别求左子树和右子树的深度，对两个深度进行比较，将最大的深度加一（根节点为一，要加进去）即得最大深度。