# 问题
将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

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
struct TreeNode* sortedArrayToBST(int* nums, int numsSize) {
    if(nums == NULL || numsSize <= 0)
        return NULL;
    struct TreeNode *root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    int mid = (numsSize - 1) / 2;
    root -> val = nums[mid];
    root -> left = sortedArrayToBST(nums, mid);
    root -> right = sortedArrayToBST(nums + mid +1, numsSize - mid - 1);
    return root;
}
```
# 心得
对于一个升序排列的有序数组转变成高度平衡二叉树，可以从中间分开，根为中间值，左子树为中间值左边的数，右子树为中间值右边的数。