# 问题
翻转一棵二叉树

# 程序

```C
struct TreeNode* invertTree(struct TreeNode* root) {
    if(root == NULL)
        return NULL;
    struct TreeNode *t;
    t = root -> left;
    root -> left = invertTree(root -> right);
    root -> right = invertTree(t);
    return root;
}
```

# 心得
如果根为空，则返回空。否则，将左子树赋值给中间值，将右子树赋值给左子树，将中间值中左子树的值赋值给右子树。