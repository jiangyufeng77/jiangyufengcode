# 问题
给定一个不含重复元素的整数数组。一个以此数组构建的最大二叉树定义如下：

二叉树的根是数组中的最大元素。
左子树是通过数组中最大值左边部分构造出的最大二叉树。
右子树是通过数组中最大值右边部分构造出的最大二叉树。
通过给定的数组构建最大二叉树，并且输出这个树的根节点。

#程序
```C
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
int findMax(int* nums,int numsSize){
    int i;
    int max = nums[0];
    int index = 0;
    for(i = 1; i < numsSize; i++)
    {
        if(nums[i] > max)
        {
            max = nums[i];
            index = i;
        }
    }
    return index;
}
struct TreeNode* constructMaximumBinaryTree(int* nums, int numsSize) {
    if(numsSize == 0)
    {
        return NULL;
    } 
    struct TreeNode *new = malloc(sizeof(struct TreeNode));
    int index = findMax(nums,numsSize);
    new -> val = nums[index];
    new -> left = constructMaximumBinaryTree(nums, index);
    new -> right = constructMaximumBinaryTree(nums + index + 1,numsSize - index - 1);
    return new; 
}
```
# 心得
在第一个程序中，定义一个变量max，用来存放最大值，并赋初值为nums[0]，通过一个for循环，比较整个数组中的数，将最大值存放到max中，并将其索引赋值到index。在第二个程序中，如果数组长度为0，返回0；否则将最大值赋给新数组的根，左右子树按照要求放置数。