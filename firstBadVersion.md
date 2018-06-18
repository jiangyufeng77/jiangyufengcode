# 问题
你是产品经理，目前正在带领一个团队开发新的产品。不幸的是，你的产品的最新版本没有通过质量检测。由于每个版本都是基于之前的版本开发的，所以错误的版本之后的所有版本都是错的。

假设你有 n 个版本 [1, 2, ..., n]，你想找出导致之后所有版本出错的第一个错误的版本。

你可以通过调用 bool isBadVersion(version) 接口来判断版本号 version 是否在单元测试中出错。实现一个函数来查找第一个错误的版本。你应该尽量减少对调用 API 的次数。
# 程序
```C
// Forward declaration of isBadVersion API.
bool isBadVersion(int version);

int firstBadVersion(int n) {
    int a = 0;
    int c = n;
    while(a <= c)
    {
        int b = a + (c - a) / 2;
        if(isBadVersion(b))
        {
            c = b - 1;
        }
        else
        {
            a = b + 1;
        }
    }
    return a;
}
```
# 心得
找第一个错误版本，可以每次都取中值，看中间这个是否是错误版本。如果是，则把高阈值降一，如果不是，则把低阈值加一，直到找到第一个错误版本。