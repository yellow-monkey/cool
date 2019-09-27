/*程序名：平均值.cpp
   功能：求3个数的平均值，演示C++简单I/O格式控制*/
#include<iostream>
#include<iomanip>
using namespace std;
int main()
{
     float num1,num2,num3;          //定义3个数
     cout<<"Please input three numbers:";
     cin>>num1>>num2>>num3;
     cout<<setw(8)<<setprecision(12);
     cout<<"The average of"<<num1<<","<<num2<<"and"<<num3;
     cout<<'is:"<<setw(20)<<(num1+num2+num3)/3<<endl;
     return 0;
}
