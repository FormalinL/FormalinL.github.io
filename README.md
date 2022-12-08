# 没什么神奇的事情的编程学习日志<br>（虽然也不一定是日志就是了）  

<a id="top">这里是顶部捏\~(￣▽￣)\~*</a>

> 开启第一次学习记录  

 ## *这次记录的是冒泡排序 -- BubbleSort*  <br>
  同时在这一次编写中我也是第一次使用到了分文件编写，也就是把不同的函数写在不同的\.cpp文件中，然后在main函数中调用   
  以下是具体函数：  

 

 	void bubblesort(int* arr, int len) {

		for (int i = 0; i < len - 1; i++)
		{
			for (int j = 0; j < len - 1 - i; j++)
			{
				if (arr[j] < arr[j + 1])
				{
					int temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
			}
		}
	}
 
 <br>

[回到顶部](#top)


## *没什么用的通讯录 -- Address Book*  <br>
做了一个通讯录，基本能实现“添加”、“显示”、“查找”、“删除”、“清除”等功能。虽然貌似没什么用，但也算是第一个完整的项目？
<br>
首先要做的是构建结构数组来容纳联系人信息

```
struct contact {
	string name;
	string gender;
	int phone_number;
	string address;
};
```

其次是构造联系人库

```
struct address_book {    //创建联系人库
	struct contact contact_arry[max];
	int m_size;
};
```

主函数就是一个简单的switch语句

```
int main()
{
	address_book kfc;
	kfc.m_size = 0;
	int select;     //选择要进行哪种功能

		while (true) {

			showMenu();
			cin >> select;

			switch (select)
			{
			case 1://显示联系人函数
				showAllContact(&kfc);
				break;
			case 2://添加联系人函数
				addContact(&kfc);
				break;
			case 3://查找联系人函数
				findContact(&kfc);
				break;
			case 4://删除联系人函数
				delectContact(&kfc);
				break;
			case 5://清空通讯录函数
				cleanAll(&kfc);
				break;
			case 6:
				//退出
				break;
			}

			if (select == 6) {
				break;
			}
			system("pause");
		
		}
}
```

添加联系人：

```
void addContact(address_book *kfc)
{
	if (kfc->m_size == max) {
		cout << "通讯录人数已满" << endl;
	};
	string name;
	cout << "联系人姓名" << endl;
	cin >> name;
	kfc->contact_arry[kfc->m_size].name = name;
	cout << "请输入联系人性别" << endl << "男" << "\t" << "女" << endl;
	string gender;
	cin >> gender;
	kfc->contact_arry[kfc->m_size].gender = gender;
	int phone_num;
	cout << "联系人电话号码" << endl;
	cin >> phone_num;
	kfc->contact_arry[kfc->m_size].phone_number = phone_num;
	cout << "请输入联系人地址" << endl;
	string address;
	cin >> address;
	kfc->contact_arry[kfc->m_size].address = address;

	kfc->m_size++;
	cout << "添加成功" << endl;
}
```

显示联系人：

```
void showAllContact(address_book* kfc) {

	for (int i = 0; i < kfc->m_size; i++)
	{
		cout << "联系人姓名:" << "\t" << kfc->contact_arry[i].name << endl;
		cout << "联系人性别：" << "\t" << kfc->contact_arry[i].gender << endl;
		cout << "联系人电话号码：" << "\t" << kfc->contact_arry[i].phone_number << endl;
		cout << "联系人住址：" << "\t" << kfc->contact_arry[i].address << endl;
		cout << endl;
	}
	system("pause");
	system("cls");
}
```

查找联系人：

```
void findContact(address_book* kfc) {
	string name;
	cout << "请输入要查找的联系人姓名" << endl;
	cin >> name;
	isExist(kfc, name);
	int re = isExist(kfc, name);
	cout << "联系人姓名:" << "\t" << kfc->contact_arry[re].name << endl;
	cout << "联系人性别：" << "\t" << kfc->contact_arry[re].gender << endl;
	cout << "联系人电话号码：" << "\t" << kfc->contact_arry[re].phone_number << endl;
	cout << "联系人住址：" << "\t" << kfc->contact_arry[re].address << endl;
	cout << endl;
}
```

其中里面用到的isExist函数是用来检测是否存在该联系人的

```
int isExist(address_book* kfc, string name) {
	for (int i = 0; i < kfc->m_size; i++) {
		if (kfc->contact_arry[i].name == name) {
			return i;
		}
		else {
			return -1;  //通过返回值来判断是否存在并在后续的删除和查找中给予下标
		}
	}
}
```

删除联系人：

```
void delectContact(address_book* kfc) {
	string name;
	cout << "请输入需要删除的联系人" << endl;
	cin >> name;

	if (isExist(kfc, name) == -1) {
		cout << "查无此人" << endl;
	}
	else {
		int re = isExist(kfc, name);
		for (int a = re; a < kfc->m_size -1; a++) {
			kfc->contact_arry[a] = kfc->contact_arry[a + 1];
		}
		kfc->m_size--;
		cout << "删除成功" << endl;
	}
}
```

最后的清空函数：

```
void cleanAll(address_book* kfc) {
	kfc->m_size = 0;
	cout << "通讯录已全部清空" << endl;
	system("pause");
	system("cls");
}
```

[回到顶部](#top)


# 知识点记录（总的来说也算是学习日志的一部分，但由于是具体的知识点，因此不太方便和其他的合并，因此单独开一个title #
[回到顶部](#top)

## class and struct ##
	class和struct本质上都是在定义一种特殊集合，目的在于方便以后使用，比如说在制作游戏中，希望对于每个玩家*player*

