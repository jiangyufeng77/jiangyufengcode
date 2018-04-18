# 问题
初始位置（0，0）处有一个机器人。给出它的一系列动作，判断这个机器人的移动路线是否形成一个圆圈，换言之就是判断它是否会移回到原来的位置。
移动顺序由一个字符串表示。每一个动作都是由一个字符来表示的。机器人有效的动作有R（右）、L（左）、U（上）和D（下），输出应为true或false，表示机器人移动路线是否成圈。
# 程序
```C
bool judgeCircle(char* moves) {
    int i;
    int x = 0,y = 0;
    int l = strlen(moves);
    for(i = 0;i < l;i++)
    {
        if(moves[i] == 'U')
        {
            y = y + 1;
        }
        else if(moves[i] == 'D')
        {
            y = y - 1;
        }
        else if(moves[i] == 'R')
        {
            x = x + 1;
        }
        else
        {
            x = x - 1;
        }
    }
    if(x == 0 && y == 0)
    {
        return true;
    }
    else 
    {
        return false;
    }
}
```
# 心得
将上下左右四个方向分别对应着x和y的数值，每走一步，就加一或减一。只有遍历后，x和y都为0，才说明可以成圈，返回true，否则就是false。
