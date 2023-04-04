# test.4_4
//结构体的声明
#include <stdio.h>
#include <stdlib.h>
struct stu
{
	//定义结构体类型
	char name[20];
	int age;
	char tele[12];
	char sex[5];
};
typedef struct stu
{


}s1,s2,s3;//全局变量
typedef struct stu
{


}stu;//重定义的类型
int main()
{
	struct stu s1;//定义结构体变量
	stu s2;//直接用stu定义变量
	return 0;
}
//嵌套结构体初始化
struct S
{
	int a;
	char c;
	char arr[20];
	double d;
};
struct T
{
	char ch[10];
	struct S s;
	char* ps;
};
int main()
{
	char arr[]="hello world";
	struct T t={"hehe",{100,'w',"hello bit",3.14},arr};
	printf("%s\n",t.ch);
	printf("%d\n",t.s.a);
	printf("%s\n",t.s.c);
	printf("%s\n",t.s.arr);
	printf("%lf\n",t.s.d);
	printf("%s\n",t.ps);
	return 0;
}
//结构体成员的访问(比较print1和print2在函数传参时的不同)
typedef struct stu
{
	char name[20];
	int age;
	char tele[12];
	char sex[5];
}stu;
void print1(stu tmp)
{
	printf("%s\n",tmp.name);
	printf("%d\n",tmp.age);
	printf("%s\n",tmp.tele);
	printf("%s\n",tmp.sex);
}
void print2(stu* ps)
{
	printf("%s\n",ps->name);
	printf("%d\n",ps->age);
    printf("%s\n",ps->tele);
	printf("%s\n",ps->sex);
}
int main()
{
	stu s={"张三",100,"15598888866","男"};
	print1(s);
	print2(&s);
	return 0;
}
//比较Debug和Release的功能不同
int main()
{
	int i = 0;
	int arr[]={1,2,3,4,5,6,7,8,9,10};
	for(i=0;i<=12;i++)
	{
		printf("hehe\n");
		arr[i] = 0;
	}
	system("pause");
	return 0;
}
//计算1！+2！+3！+........+n!
int main()
{
	int i = 0;
	int n = 0;
	int sum = 0;
	int ret = 1;
	for(i=0;i<=n;i++)
	{
		int j = 0;
		for(j=1;j<=i;j++)
		{
			ret *= j;
		}
		sum += ret;
	}
	system("pause");
	return 0;
}
void test2()
{
	printf("hehe\n");
}
void test1()
{
	test2();
}
void test()
{
	test1();
}
int main()
{
	test();
	return 0;
}
