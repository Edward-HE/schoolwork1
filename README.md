# C语言大作业：四则运算练习

## 题目要求
```
题目：小学生测验 面向小学1~2年级学生，随机选择两个整数进行四则运算，要求学生解答。 功能要求： 
（1）电脑随机出题，题目数用户设置，满分100分，程序结束时显示学生得分； 
（2）确保算式没有超出1~2年级的水平，只允许进行100以内的四则运算，不允许两数或运算结果超出0~100的范围，负数更是不允许的； 
（3）每道题学生有两次机会输入答案，当学生输入错误答案时，提醒学生重新输入，如果两次机会结束则输出正确答案； 
（4）对于每道题，学生第一次输入正确答案得该题满分，第二次输入正确答案得该题一半的分，否则不得分； 
（5）总成绩90以上显示“SMART” ,80-90显示“GOOD”，70-80显示“OK, 60-70显示“PASS”，60以下“TRY AGAIN”
（6）保存学生做过的题目，保存的细节自己考虑。可以加载浏览。
注意：
程序运行后，
1.注册、登录。登录要求输入用户名，密码，三次机会。（注册信息应写入文件，写入时，应检查用户名是否重复）

```

`4月16日19:00`开始，`4月20日11:32`结束。
可执行代码共计`346`行。主要难点为`注册和登录`和`错题集`。
### 注册和登录
采用结构体数组，并储存在一个txt文件中

```c
typedef struct users_info {
	char name[50];
	char pswd[20];
} users_info;
```

### 错题集
采用txt文件实现，实现思路如下：

```c
scanf("%s", &a.name);
strcpy(login_name_wq, a.name);
strcat(login_name_wq, ".txt");//用输入的用户名创建.txt文件
fp3 = fopen(login_name_wq, "w+");
fclose(fp3);
```
错题写入方法：
```c
char tmp1[256];
memset(tmp1, 0, sizeof(tmp1));//清空垃圾数据
sprintf(tmp1, "   %d%c%d= %d , 正确答案为： %d\n", num1,operation,num2,uanswer,ranswer);//错题写入错题集
fp3 = fopen(login_name_wq, "a");
fwrite(tmp1, 1, strlen(tmp1), fp3);
fclose(fp3);
```

错题查看方法：

```c
fp3 = fopen(login_name_wq, "a+");
while (!feof(fp3))
putchar(fgetc(fp3));
fclose(fp3);
```


