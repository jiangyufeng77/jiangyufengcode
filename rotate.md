# 问题
给定一个 n × n 的二维矩阵表示一个图像。

将图像顺时针旋转 90 度。

说明：

你必须在原地旋转图像，这意味着你需要直接修改输入的二维矩阵。请不要使用另一个矩阵来旋转图像。
# 程序
```C
void rotate(int** matrix, int matrixRowSize, int *matrixColSizes) {
    int i,j;
    int num = 0;
    int t = 0;
	for (i = 0; i < matrixRowSize / 2; i++)
	{
        num = matrixRowSize - 2 * i - 1;
		for (j = 0; j < num; j++)
		{
			t = matrix[matrixRowSize - i - 1 - j][i];
			matrix[matrixRowSize - i - 1 - j][i] = matrix[matrixRowSize - i - 1][matrixRowSize - 1 - i - j];
			matrix[matrixRowSize - i - 1][matrixRowSize - 1 - i - j] = matrix[i + j][matrixRowSize - i - 1];
			matrix[i + j][matrixRowSize - i - 1] = matrix[i][i + j];
			matrix[i][i + j] = t;
		}
	}
}
```
# 心得
看所给示例得到规律，设定一个中间变量t，从左下角开始进行两个for循环，找到旋转后的位置，然后将旋转前的位置上的数赋值给新位置，借助中间变量依次进行5次，即可得到一个顺时针旋转90后的数组。