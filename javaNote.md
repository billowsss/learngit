#java
Math.max(int a,int b)


##一.java基本数据类型
Java的两大数据类型:
###1.1内置数据类型 
八种基本类型：六种数字类型（四个整数型，两个浮点型），一种字符类型，还布尔型。
* byte		8位，有符号的，最小值是-128（-2^7）~最大值是127（2^7-1）；byte类型用在大型数组中节约空间，主要代替整数，因为byte变量占用的空间只有int类型的四分之一
* short		short数据类型是16位、有符号的以二进制补码表示的整数，最小值是-32768（-2^15）；最大值是32767（2^15 - 1）；
Short数据类型也可以像byte那样节省空间。一个short变量是int型变量所占空间的二分之一；默认值是0。
* long	long数据类型是64位、有符号的以二进制补码表示的整数；最小值是-9,223,372,036,854,775,808（-2^63）；最大值是9,223,372,036,854,775,807（2^63 -1）；这种类型主要使用在需要比较大整数的系统上；默认值是0L 
* int	nt数据类型是32位、有符号的以二进制补码表示的整数；
最小值是-2,147,483,648（-2^31）；
最大值是2,147,485,647（2^31 - 1）；
一般地整型变量默认为int类型；
默认值是0；
* double	double数据类型是双精度、64位、符合IEEE 754标准的浮点数；
浮点数的默认类型为double类型；
double类型同样不能表示精确的值，如货币；
默认值是0.0f
* float		float数据类型是单精度、32位、符合IEEE 754标准的浮点数；
float在储存大型浮点数组的时候可节省内存空间；
默认值是0.0f；
浮点数不能用来表示精确的值，如货币 
* char	char类型是一个单一的16位Unicode字符,占两个字节，0~65535
最小值是’\u0000’（即为0）；
最大值是’\uffff’（即为65,535）；
char数据类型可以储存任何字符；
char类型存储汉字时查询Unicode
例子：char letter = ‘A’。
*  bool
###1.2引用数据类型 
* 引用类型变量由类的构造函数创建，可以使用它们访问所引用的对象。这些变量在声明时被指定为一个特定的类型，比如Employee、Pubby等。变量一旦声明后，类型就不能被改变了。
* 对象、数组都是引用数据类型。
* 所有引用类型的默认值都是null。
* 一个引用变量可以用来引用与任何与之兼容的类型。
例子：Animal animal = new Animal(“giraffe”)。

###java常量
常量指不能改变的量。 在Java中用final标志，声明方式和变量类似，通常使用大写字母表示常量

###转义字符
\n	换行 (0x0a)
\r	回车 (0x0d)
\f	换页符(0x0c)
\b	退格 (0x08)
\s	空格 (0x20)
\t	制表符
\"	双引号
\'	单引号
\\	反斜杠
\ddd	八进制字符 (ddd)
\uxxxx	16进制Unicode字符 (xxxx)
##java基础语法  
* 对象：对象是类的一个实例，有'状态'和'行为'。
* 类：描述一类对象的的状态和行为。
* 方法：方法就是行为，一个类可以有很多方法。  
* 实例变量：每个对象都有独特的实例变量，对象的状态有这些实例变量的值决定。

##第一个java程序  
	helloworld

##基础语法
编写java程序时，应注意：
* 大小写敏感。
* 类名首字母需大写，eg: 'public class MyFirst'  
* 方法名应以小写字母开头，若包含多个单词，则后面的单词首字母应大写。
* 源文件名必须和类名相同。
* 主方法入口由'public static void main(String args[])'方法开始的。



##java标识符
java所有的组成部分都需要名字。类名、变量名以及方法名都被称为标识符。  
java标识符注意项：
* 所有的标识符都应该以字母（A-Z或者a-z）,美元符（$）、或者下划线（_）开始。  
* 首字符之后可以是任何字符的组合。  
* 关键字不能用作标识符。  
* 标识符是大小写敏感的。

##java修饰符
Java可以使用修饰符来修饰类中方法和属性。主要有两类修饰符：
* 可访问修饰符 : public , protected, private,default
* 不可访问修饰符 : final, abstract, strictfp

##java变量
Java中主要有如下几种类型的变量：
* 局部变量
* 类变量（静态变量）
* 成员变量（非静态变量）

##循环
###for each

##java数组
数组是储存在堆上的对象，可以保存多个同类型变量
###数组打印方法
* for循环打印
* for each循环
* 利用Array类的toString方法
###数组逆序
###数组排序
* 选择排序 selectionSort
数组的每个元素都进行比较

	public class selectionSort {
	    public static void main(String[] args) {
	        int[] arr = {1, 2, 6, 5, 9, 8};
	        selectionSort(arr);
	        printArray(arr);
	    }
	
	    public static void selectionSort(int[] arr) {
	        int temp;
	
	        for (int i = 0; i < arr.length - 1; i++) {
	            for (int j = i + 1; j < arr.length; j++) {
	                if (arr[i] > arr[j]) {
	                    temp = arr[i];
	                    arr[i] = arr[j];
	                    arr[j] = temp;
	                }
	            }
	        }
	    }
	
	    public static void printArray(int[] arr) {
	        System.out.print("{");
	
	        // int[] arr ={1,2,6,5,8,9};
	        //先打印出{  接下来每步打印出 arr[i], 输出到末尾(判定条件：i==arr.length-1)打印 arr[arr.length-1]}
	        for (int i = 0; i < arr.length; i++) {
	            
	            if (i == arr.length - 1) {
	                System.out.print(arr[i] + "}");
	            } else {
	                System.out.print(arr[i] + " ");
	            }
	        }
	    }
	}	


* 冒泡排序 bubbleSort
相邻元素比较

	public class bubbleSort {
	    public static void main(String[] args) {
	
	        int[] arr = {1, 2, 6, 5, 9, 8};
	        bubbleSort(arr);
	        printArray(arr);
	    }
	    public static void bubbleSort(int[] arr){
	
	        for (int i = 0; i < arr.length - 1; i++) {
	            for (int j = 0; j < arr.length-1-i; j++) {
	                if (arr[j] > arr[j+1]) {
	                    int  temp = arr[j];
	                    arr[j] = arr[j+1];
	                    arr[j+1] = temp;
	                }
	            }
	        }
	    }
	
	    public static void printArray(int[] arr) {
	        System.out.print("{");
	        // int[] arr ={1,2,6,5,8,9};
	        //先打印出{  接下来每步打印出 arr[i], 输出到末尾(判定条件：i==arr.length-1)打印 arr[arr.length-1]}
	        for (int i = 0; i < arr.length; i++) {
	
	            if (i == arr.length - 1) {
	                System.out.print(arr[i] + "}");
	            } else {
	                System.out.print(arr[i] + " ");
	            }
	        }
	    }
	
	}
* 二分查找/折半 binarySearch
		前提：被查找的数组，必须是有序数组

思想：

	(max+min)/2；折半前提 min <= max
	折半后的指针索引和被查找，比较
	如果 被查找的元素>中间索引上的元素，小指针=中间指针+1
	如果 被查找的元素<中间索引上的元素，大指针=中间指针-1
	当小指针索引>大指针索引，循环结束，没找到，返回 -1
	元素等于数组中间索引上的元素，也结束，结果就是中间索引
代码如下：

	public static int binarySearch(int[] arr,int key){

		int min =0;
		int mid =0;
		int max =arr.length-1;

		//循环折半条件是 min<=max
		while(min<=max){
			//计算中间索引
			min =(min+max)/2;
			//被查找元素key与中间索引元素进行比较
			if(key>arr[min]){
			   min = mid +1;	
			}else if(key<arr[min]){
				max = mid -1;
			}else{
				return mid;
			}
		}
		 return -1;
	}
##java枚举	
Java 5.0引入了枚举，枚举限制变量只能是预先设定好的值。使用枚举可以减少代码中的bug。  
注意：枚举可以单独声明或者声明在类里面。方法、变量、构造函数也可以在枚举中定义。

例如，我们为果汁店设计一个程序，它将限制果汁为小杯、中杯、大杯。这就意味着它不允许顾客点除了这三种尺寸外的果汁。	
class FreshJuice {
   enum FreshJuiceSize{ SMALL, MEDUIM, LARGE }
   FreshJuiceSize size;
}

public class FreshJuiceTest {
   public static void main(String args[]){
      FreshJuice juice = new FreshJuice();
      juice.size = FreshJuice. FreshJuiceSize.MEDUIM ;
   }
}

##java关键字
Java保留字。这些保留字不能用于常量、变量、和任何标识符的名称

##java注释
* 单行注释  /*这是单行注释 */
* 多行注释  /*这是
		    *一个多行注释
			*/

##java空行
空白行，或者有注释的的行，Java编译器都会忽略掉。

##java基础语法

###类
具有状态和属性，是引用数据类型

	修饰符 class 返回值类型 类名｛

		属性1;
		...；
		属性n;

	｝


###类的使用格式
####创建类的对象
			数据类型  变量名 = new 数据类型(); //创建类的对象
####访问属性：
			变量名.属性 //后期会采取调用方法的方式来完成对属性的访问
####调用方法

###ArrayList集合

####ArrayList的创建
		import java.util.ArrayList;	//导包
		ArrayList<元素数据类型>  变量名 = new ArrayList<元素数据类型>();
* 集合中存储的元素，只能为<>括号中指定的数据类型元素；
* “<要存储元素的数据类型>”中的数据类型必须是引用数据类型，不能是基本数据类型；


'''下面给出8种基本数据类型所对应的引用数据类型表示形式'''

|基本数据类型|对应的引用数据类型表现形式|
|:-:|:-:|
|byte	|Byte|
|short	|Short|
|Int	|Integer|
|long	|Long|
|float	|Float|
|double	|Double|
|char	|Character|
|boolean|Boolean|


####ArrayList常用方法
* 指定元素添加到集合末尾
	ArrayListName.add(element)
* 返回集合中指定位置上的元素
	ArrayListName.get(int index) //index不要越界
* 返回集合中指定位置上的元素
	ArrayListName.size()

补充：
* 将指定元素obj插入到集合中指定的位置
	ArrayListName.add(int index，element)
* 从集合中删除指定index处的元素，返回该元素
	ArrayListName.remove(int index)
* 清空集合中所有元素
	ArrayListName.clear（）
* 用指定元素obj替代集合中指定位置上的元素
	ArrayListName.set(int index element)

	TIPS:获取数组的长度是用.length属性；获取字符串长度是length()方法

###循环
###ASCII编码表

ASCII码|十进制
-|-
|数字0~9| 48~57|
|字母a~z|97~122
|字母A~Z||65~90


ASCII表[ASCII图片](https://baike.baidu.com/pic/ASCII/309296/0/c2fdfc039245d688c56332adacc27d1ed21b2451?fr=lemma&ct=single#aid=0&pic=c2fdfc039245d688c56332adacc27d1ed21b2451)

##继承
在Java中，一个类可以由其他类派生。如果你要创建一个类，而且已经存在一个类具有你所需要的属性或方法，那么你可以将新创建的类继承该类。

利用继承的方法，可以重用已存在类的方法和属性，而不用重写这些代码。被继承的类称为超类（super class），派生类称为子类（subclass）。

##接口
在Java中，接口可理解为对象间相互通信的协议。接口在继承中扮演着很重要的角色。

接口只定义派生要用到的方法，但是方法的具体实现完全取决于派生类。