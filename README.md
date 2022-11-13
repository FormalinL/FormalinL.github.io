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
