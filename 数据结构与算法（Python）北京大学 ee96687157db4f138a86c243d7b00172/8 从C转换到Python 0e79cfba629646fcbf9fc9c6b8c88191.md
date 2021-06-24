# 8. 从C转换到Python

```c
#include <stdio.h>

int main()
{
		// say hello
		printf("Hello World!\n")
}
```

1 - Compile 编译到机械码

2 - Link 与各种库链接

3 - Execute 执行目标程序

```python
def main():
		# say hello
		print("Hello World!")

main() 
```

1 - Run! 跑代码

main都是太罗嗦了，一行ok

## C：帮高斯的同学回家

```c
#include <stdio.h>

int main()
{
		int s, i;
		s = 0;
		//adding nums 1 to 100
		for (i = 0; i < 100; i++)
		{
				s += (i + 1);
		}
		printf("Sum= %d", s)
}
```

```python
s = 0
for i in range(100):
		s += (i + 1)
print("Sum=", s)
```

少了很多变量的声明

## C：检验素数

```c
#include <stdio.h>
#include <math.h>

int main()
{
    int n, i, flag = 0;
    printf("Please input number: ");
    scanf("%d", &n);
    for (i = 2; i < sqrt(n); i++)
        if (n % i == 0)
        {
            flag = 1;
            break;
        }
    if (flag == 1)
        printf("%d is Not a prime number.\n", n);
    else
        printf("%d is a prime number.\n", n);
    system("pause");
}
```

```python
from math import sqrt

n = int(input("Please input number:"))

for i in range(2, int(sqrt(n))):
    if n % i == 0:
        print(f"{n} is Not prime number.")
        break
else:
    print(f"{n} is prime number.")
```

## C: 打印一个朴素的三角形

```c
#include <stdio.h>

int main()
{
    int n, i, j;
    printf("Please input number: ");
    scanf("%d", &n);
    for (i=0; i < n; i++)
    {
        for (j=0; j < i; j++)
        {
            printf("*");
        printf("\n");
        }
    }
    system("pause");
}
```

```python
n = int(input("Please input number: "))
for i in range(n):
    print("*" * i)
```

---