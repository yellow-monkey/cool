# include < iostream >
# include < string>
using namespace std;

//定义虚基类Person
class Person
{
public:
	
	Person(char * name, char sex, char * ID, char * birthday)
	{
		strcpy_s(this->name, strlen(name) + 1, name);        //VS下用strcpy_s
		this->sex = sex;
		strcpy_s(this->ID, strlen(ID) + 1, ID);
		strcpy_s(this->birthday, strlen(birthday) + 1, birthday);
	}
	void display()
	{
		cout << " name:" << this->name << endl;
		cout << " sex:" << this->sex << endl;
		cout << " ID:" << this->ID << endl;
		cout << " birthday:" << this->birthday << endl;
	}
private:
	char name[20];   //姓名
	char sex;   //性别
	char ID[20];   //身份证号
	char birthday[12];     //出生年月
};

class Teacher :virtual public Person //定义派生类Teacher
{
public:
	//定义构造函数	
	
	Teacher(char *position, char *name, char sex, char *ID, char *birthday) :Person(name, sex, ID, birthday)
	{
		strcpy_s(this->position, strlen(position) + 1, position);
	}

	//定义输出函数
	void display()
	{
		cout << "position:" << this->position << endl;
	}
private:
	char position[12];		//职称
};

class Student :virtual public Person	//定义派生类Student
{
public:

	//定义构造函数	
	Student( char *major, char *name, char *ID, char sex, char *birthday) :Person(name, sex, ID, birthday)
	{
		strcpy_s(this->major, strlen(major) + 1, major);
	}

	//定义输出函数
	void display()
	{
		cout << "major:" << this->major << endl;
	}

private:
	char major[20];		//专业
};

class Stu_Teach :public Teacher, public Student  //定义在职读书教师类Stu_Teach
{
public:
	//定义构造函数	
	Stu_Teach(char *name, char sex, char *ID, char *birthday, char *position, char *major) :Teacher(position, name,sex, ID,  birthday ), Student(major, name,  ID,sex, birthday), Person(name, sex, ID, birthday)	{}
	

	//定义输出函数
    void display()
	{
		Person::display();
		Student::display();
		Teacher::display();


	}
};
int main()
{
	Stu_Teach ST("Liu xiaopeng",  'M',"428120198005272487", "1976-05-27", "Computer Science", "Professor");
	ST.display();
	
	system("pause");
  return 0;
}

