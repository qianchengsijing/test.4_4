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
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>
int main()
{
	//int i = 0;
	int arr[]={1,2,3,4,5,6,7,8,9,10};
	int i = 0;

	for(i=0;i<=12;i++)
	{
		printf("hehe\n");
		arr[i] = 0;
	}

	return 0;
}
int main()
{
	//对比Debng和Release版本的不同
地址在栈中是先使用高地址，再使用低地址
	int i = 0;
	int arr[]={1,2,3,4,5,6,7,8,9,10};
	printf("%p\n",&i);
	printf("%p\n",arr);
	system("pause");
	return 0;
}
实现strcpy函数
void my_strcpy (char* dest,char* src)//第一种算法
{
	//交换b i t
	while(*src != '\0')
	{
	    *dest = *src;
	    src++;
	    dest++;
	}
	*dest = *src;//最后交换\0
}
void my_strcpy (char* dest,char* src)//第二种算法（优化）
{
	while(*dest++ = *src++)//先解引用使用再++
	{
		;
		//*dest++ == *src++;
	   /* *dest = *src;
	    src++;
	    dest++;*/
	}
	*dest = *src;
}
void my_strcpy (char* dest,char* src)//第三种算法（再优化）
{
	assert(dest != NULL);//断言，引用头文件#include <assert.h>
	assert(src != NULL);//断言(检查指针的有效性）
	while(*dest++ = *src++)
	{
	   ;
	}
	*dest = *src;
}
void my_strcpy (char* dest,const char* src)//第四种算法（再优化）
{
	assert(dest != NULL);
	assert(src != NULL);
	//while(*src++ = *dest++)//const修饰*src,不能改变*src的值
	while(*dest++ = *src++)
	{
	   ;
	}
	*dest = *src;
}
char* my_strcpy (char* dest,const char* src)//第四种算法（再优化）有返回类型
{
	char* ret = dest;//用ret接收目的地指针的地址
	assert(dest != NULL);
	assert(src != NULL);
	
	while(*dest++ = *src++)
	{
	   ;
	}
	*dest = *src;
	return ret;//返回dest的地址（arr1）给主函数打印
}
int main()
{
	char arr1[]="##############";
	char arr2[]="bit";//b i t \0
	my_strcpy(arr1,arr2);
	//my_strcpy(arr1,NULL);//若为这种情况，需要先用assert判断指针的可使用性
	//strcpy(arr1,arr2);
	printf("%s\n",arr1);
	return 0;
}
int main()
{
	const int num = 10;
	int n = 20;
	const int* p = &num;
	//const 放在指针变量*左边时，修饰*p，不能通过p来改变*p的值，可以改变p
	int *const p = &num;
	//const 放在指针变量*y右边时，修饰p，不能改变p的地址，可以改变*p
	*p = 20;
	p = &n;
	printf("%d\n",num);
	return 0;
}
int my_strlen (const char* str)
{
	int count = 0;
	assert(str != NULL);
	while(*str != '\0')
	{
		count++;
		str++;
	}
	return count;
}
int main()
{
	char arr[]="abcdef";
	int len = my_strlen(arr);
	printf("%d\n",len);
	return 0;
}
