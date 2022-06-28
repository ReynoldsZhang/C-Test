```c++
#include<iostream>
using namespace std;
/*
main是个程序的入口
每个程序都必须有这么一个函数
有且只有一个
*/
#include <string> //用c++风格字符串时，要包含这个头文件

//1.#define 宏常量
#define Day 7
int main()
{
    /*
    //goto 标记；
	// 标记：
	//可以无条件跳转语句 倘若此标记存在，则直接略过所有代码直到出现标记位置开始运行
	cout << 1 << endl;
	goto FLAG;
	cout << 2 << endl;
	cout << 3 << endl;
	FLAG:
	cout << 4 << endl;
    */
    
    
    //循环语句类似于java
    //switch语句类似于java
    //if语句类似于java
    
    
	/*
	//类似于python
	int a = 0;
	int b = 0;
	a += 2;
	cout << a << endl;
	a -= 1;
	cout << a << endl;
	a *= 2;
	cout << a << endl;
	a /= 2;
	cout << a << endl;
	a %= 2;
	cout << a << endl;
	*/
    
    /*
	int a = 0;
	int b = 0;
	cout << a++ << endl;//输出a并之后加一
	cout << ++a << endl;//先给a加一再输出
	cout << b-- << endl;//同理
	cout << --b << endl;//同理
	*/
    
    
    /*   无法一起使用
    cin >> 变量
    手动赋值
    //1. 整形
	int a1 = 0;
	cout << "请给整形变量a1赋值：" << endl;
	cin >> a1; 
	cout << "整形变量a =" <<
	a1 << endl;
	
	
	//2. 浮点型
	flaot f = 3.14f;
	cout << "请给浮点型变量f 赋值："<<endl;
	cin >> f;
	cout << "浮点型变量f = " << f << endl;
	
	//3. 字符型
	/ch = 'a';
	cout << "请给字符型变量ch赋值"<< endl;
	cin >> ch;
	cout << "字符型变量ch =" << ch <<endl; 
	
	//4. 字符串型
	string str = "hello"
	cout << "请给字符串变量str赋值"<< endl;
	cin>>str;
	cout << "字符串str = "<< str<< endl; 
	
	//5. 布尔类型 
	bool flag = false;
	cout <<"请给字符串变量false赋值"<< endl;
	cin >> false;
	cout <<"字符串变量false = " <<flag <<endl;
	*/ 
	
     //1. 创建bool数据类型
	bool flag = true; 
	cout << flag << endl;
	
	flag = false;
	cout << flag << endl;
	
	//本质上 1代表真 0代表假 
	
	//2. 查看bool类型内存所占空间 
	
	cout << "bool 类型所占的内存空间:" << sizeof(bool) << endl; 
    //c风格文字字符串
    //注意事项  1.char 字符串名 []
    //注意事项  2.等号后面 要用双引号 包含起来字符串
    char str [] = "hollow world";
    cout << str << endl;
    
    //c++风格字符串
    string str2 = "hollow world";
    cout << str2 << endl;
    
    // 单精度 float
    // 双精度 double
    // 默认情况下 输出一个小数，会显示出6位有效数字

    float f1 = 3.14f;

    cout << "fi =" << f1 << endl;

    double d1 = 3.14;

    cout << "di =" << d1 << endl;

    // 统计float和double所占用的内存空间
    cout << "float占用的内存空间为:" << sizeof(float) << endl;
    cout << "double占用的内存空间为:" << sizeof(double) << endl;

    //科学计数法
    float f2 = 3e2; //3* 10 ^ 2;
    cout << "f2 =" << f2 << endl;
    float f3 = 3e-2;// 3* 0.1 ^ 2;
    cout << "f3 =" << f3 << endl;

    //可以利用sizeof去求出数据类型占用内存大小
    //语法：sizeof （数据类型/ 变量）
    cout << "short占用的内存空间为：" << sizeof(short) << endl;
    cout << "int占用的内存空间为：" << sizeof(int) << endl;
    cout << "long占用的内存空间为：" << sizeof(long) << endl;
    cout << "long long占用的内存空间为：" << sizeof(long long) << endl;


    //短整形 (-32768 ~ 32767)
    short num1 = 32768;

    //整形
    int num2 = 32768;

    //长整形
    long num3 = 10;

    //长长整形
    long long num4 = 10;

    cout << "num1 = " << num1 << endl;
    cout << "num2 = " << num2 << endl;
    cout << "num3 = " << num3 << endl;
    cout << "num4 = " << num4 << endl;

    //标识符不可以是关键字
    //int int = 10;

    //标识符是由字母、数字、下划线构成
    int abc = 10;
    int _abc = 20;
    int _abc123 = 30;

    //标识符的第一个字符只能是字母或者下划线
    //int 123abc = 40;

    //标识符区分大小写
    int aaa = 100;
    cout << aaa << endl;
    //cout << AAA << endl; // AAA和aaa不是同一个名称

    //Day=14; //错误，Day是常量，一旦修改就会报错
    cout << "一周总共有：" << Day << " 天" << endl;

    //2.const修饰的变量
    const int month = 12;
    //month = 24;// 错误，const修改的变量也称为常量
    
    cout << "一年总共有：" << month << " 个月份" << endl;

    //这一行代码的含义，就是在屏幕中输出hellow world
    cout << "hellow world" << endl;

    // 变量创建的语法：数据类型 变量名称 = 变量初始值
    //不要用关键字给变量或常量其名称
    // int int = 10; 错误，第二个int是关键字，不可以作为变量的名称
    int a = 10;
    cout << "a=" << a << endl;

    system("pause");

    return 0;
}

```
