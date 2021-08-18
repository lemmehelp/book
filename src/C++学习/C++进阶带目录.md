<a name="index">**Index**</a>

<a href="#0">C++ 类 & 对象</a>  
&emsp;&emsp;<a href="#1">一、C++类的定义</a>  
&emsp;&emsp;<a href="#2">二、C++定义对象（类似于python中的类的实例化）</a>  
&emsp;&emsp;&emsp;<a href="#3">访问数据成员</a>  
&emsp;&emsp;<a href="#4">三、类 & 对象详解</a>  
&emsp;&emsp;&emsp;<a href="#5">1、类的成员函数</a>  
&emsp;&emsp;&emsp;<a href="#6">2、类访问修饰符</a>  
&emsp;&emsp;&emsp;<a href="#7">3、构造函数与析构函数</a>  
&emsp;&emsp;&emsp;<a href="#8"> 4、C++拷贝构造函数</a>  
&emsp;&emsp;&emsp;<a href="#9"> 5、C++友元函数(相当于给开后门，给某些函数特定权利可以访问私有资源)</a>  
&emsp;&emsp;&emsp;<a href="#10">6、内联函数</a>  
&emsp;&emsp;&emsp;<a href="#11">7、C++ this指针</a>  
&emsp;&emsp;&emsp;<a href="#12">8、指向类的指针</a>  
&emsp;&emsp;&emsp;<a href="#13">9、C++类的静态成员</a>  
&emsp;&emsp;&emsp;<a href="#14">10、静态函数成员</a>  

# <a name="0">C++ 类 & 对象</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

C++ 在 C 语言的基础上增加了面向对象编程，C++ 支持面向对象程序设计。类是 C++ 的核心特性，通常被称为用户定义的类型。

类用于指定对象的形式，它包含了数据表示法和用于处理数据的方法。类中的数据和方法称为类的成员。函数在一个类被称为类的成员。

### <a name="1">一、C++类的定义</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

类定义是以关键字 **class** 开头，后跟类的名称。类的主体是包含在一对花括号中。类定义后必须跟着一个分号或一个声明列表。例如，我们使用关键字 **class** 定义 Box 数据类型，如下所示：

```C++
class Box
{
   public:
      double length;   // Length of a box
      double breadth;  // Breadth of a box
      double height;   // Height of a box
};
```

关键字 **public** 确定了类成员的访问属性。在类对象作用域内，公共成员在类的外部是可访问的。您也可以指定类的成员为 **private** 或 **protected**，这个后面会展开介绍。

### <a name="2">二、C++定义对象（类似于python中的类的实例化）</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

类提供了对象的蓝图，所以基本上，对象是根据类来创建的。声明类的对象，就像声明基本类型的变量一样。下面的语句声明了类 Box 的两个对象：

```C++
Box Box1;          // 声明 Box1，类型为 Box
Box Box2;          // 声明 Box2，类型为 Box
```

Box1和Box2都有属于他们各自的数据成员

#### <a name="3">访问数据成员</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

类的对象的公共数据成员可以使用**直接成员访问运算符 (.)** 来访问。为了更好地理解这些概念，让我们尝试一下下面的实例：

```C++
#include <iostream>

using namespace std;

class Box
{
   public:
      double length;   // 长度
      double breadth;  // 宽度
      double height;   // 高度
};

int main( )
{
   Box Box1;        // 声明 Box1，类型为 Box
   Box Box2;        // 声明 Box2，类型为 Box
   double volume = 0.0;     // 用于存储体积
 
   // box 1 详述
   Box1.height = 5.0; 
   Box1.length = 6.0; 
   Box1.breadth = 7.0;

   // box 2 详述
   Box2.height = 10.0;
   Box2.length = 12.0;
   Box2.breadth = 13.0;

   // box 1 的体积
   volume = Box1.height * Box1.length * Box1.breadth;
   cout << "Box1 的体积：" << volume <<endl;

   // box 2 的体积
   volume = Box2.height * Box2.length * Box2.breadth;
   cout << "Box2 的体积：" << volume <<endl;
   return 0;
}
```

**需要注意的是，私有的成员和受保护的成员不能使用直接成员访问运算符 (.) 来直接访问。**

### <a name="4">三、类 & 对象详解</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

到目前为止，我们已经对 C++ 的类和对象有了基本的了解。下面的列表中还列出了其他一些 C++ 类和对象相关的概念，可以点击相应的链接进行学习。

| 概念                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [类成员函数](https://www.w3cschool.cn/cpp/cpp-class-member-functions.html) | 类的成员函数是指那些把定义和原型写在类定义内部的函数，就像类定义中的其他变量一样。 |
| [类访问修饰符](https://www.w3cschool.cn/cpp/cpp-class-access-modifiers.html) | 类成员可以被定义为 public、private 或 protected。默认情况下是定义为 private。 |
| [构造函数 & 析构函数](https://www.w3cschool.cn/cpp/cpp-constructor-destructor.html) | 类的构造函数是一种特殊的函数，在创建一个新的对象时调用。类的析构函数也是一种特殊的函数，在删除所创建的对象时调用。 |
| [C++ 拷贝构造函数](https://www.w3cschool.cn/cpp/cpp-copy-constructor.html) | 拷贝构造函数，是一种特殊的构造函数，它在创建对象时，是使用同一类中之前创建的对象来初始化新创建的对象。 |
| [C++ 友元函数](https://www.w3cschool.cn/cpp/cpp-friend-functions.html) | **友元函数**可以访问类的 private 和 protected 成员。         |
| [C++ 内联函数](https://www.w3cschool.cn/cpp/cpp-inline-functions.html) | 通过内联函数，编译器试图在调用函数的地方扩展函数体中的代码。 |
| [C++ 中的 this 指针](https://www.w3cschool.cn/cpp/cpp-this-pointer.html) | 每个对象都有一个特殊的指针 **this**，它指向对象本身。        |
| [C++ 中指向类的指针](https://www.w3cschool.cn/cpp/cpp-pointer-to-class.html) | 指向类的指针方式如同指向结构的指针。实际上，类可以看成是一个带有函数的结构。 |
| [C++ 类的静态成员](https://www.w3cschool.cn/cpp/cpp-static-members.html) | 类的数据成员和函数成员都可以被声明为静态的。                 |

#### <a name="5">1、类的成员函数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

​	类的成员函数是指那些把定义和原型写在类定义内部的函数，就像类定义中的其他变量一样。类成员函数是类的一个成员，它可以操作类的任意对象，可以访问对象中的所有成员。

**类的成员函数有两种定义方式：**

- 直接在定义类的时候在类的内部定义

  ```C++
  class Box
  {
     public:
        double length;      // 长度
        double breadth;     // 宽度
        double height;      // 高度
     
        double getVolume(void)
        {
           return length * breadth * height;
        }
  };
  ```

- 此外，成员函数也可以在类的外部定义，此时需要在定义类的时候在类的内部首先对函数进行声明，然后再用**::**（**范围解析运算符**）来定义，

  ```C++
  class Box
  {
     public:
        double length;         // 长度
        double breadth;        // 宽度
        double height;         // 高度
        double getVolume(void);// 返回体积
  };
  double Box::getVolume(void)
  {
  	return length *breadth*height;
  }
  ```

> 这里需要强调的是，范围解析运算符（::）需要跟在类名的后面
>
> 而点运算符（.）则需要跟在对象名称后面

```C++
Box myBox;          // 创建一个对象

myBox.getVolume();  // 调用该对象的成员函数
```

一个例子🌰：

```C++
#include <iostream>

using namespace std;

class Box
{
   public:
      double length;         // 长度
      double breadth;        // 宽度
      double height;         // 高度

      // 成员函数声明
      double getVolume(void);
      void setLength( double len );
      void setBreadth( double bre );
      void setHeight( double hei );
};

// 成员函数定义
double Box::getVolume(void)
{
    return length * breadth * height;
}

void Box::setLength( double len )
{
    length = len;
}

void Box::setBreadth( double bre )
{
    breadth = bre;
}

void Box::setHeight( double hei )
{
    height = hei;
}

// 程序的主函数
int main( )
{
   Box Box1;                // 声明 Box1，类型为 Box
   Box Box2;                // 声明 Box2，类型为 Box
   double volume = 0.0;     // 用于存储体积
 
   // box 1 详述
   Box1.setLength(6.0); 
   Box1.setBreadth(7.0); 
   Box1.setHeight(5.0);

   // box 2 详述
   Box2.setLength(12.0); 
   Box2.setBreadth(13.0); 
   Box2.setHeight(10.0);

   // box 1 的体积
   volume = Box1.getVolume();
   cout << "Box1 的体积：" << volume <<endl;

   // box 2 的体积
   volume = Box2.getVolume();
   cout << "Box2 的体积：" << volume <<endl;
   return 0;
}
```

#### <a name="6">2、类访问修饰符</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

​	数据隐藏是面向对象编程的一个重要特点，它防止函数直接访问类类型的内部成员。类成员的访问限制是通过在类主体内部对各个区域标记 **public、private、protected** 来指定的。关键字 public、private、protected 称为访问说明符。

一个类可以有多个 public、protected 或 private 标记区域。**每个标记区域在下一个标记区域开始之前或者在遇到类主体结束右括号之前都是有效的**。**成员和类的默认访问修饰符是 private。**

```C++
class Base{
	public:
	//public members go here
	
	protected:
	//protected members go here
	
	private:
	//private members go here
};
```

- 公有（public）成员

  **公有成员**是在程序中类的外部是可访问的。您可以不使用任何成员函数来设置和获取公有变量的值，如下所示：

  ```C++
  #include <iostream>
   
  using namespace std;
   
  class Line
  {
     public:
        double length;
        void setLength( double len );
        double getLength( void );
  };
   
  // 成员函数定义
  double Line::getLength(void)
  {
      return length ;
  }
   
  void Line::setLength( double len )
  {
      length = len;
  }
   
  // 程序的主函数
  int main( )
  {
     Line line;
   
     // 设置长度
     line.setLength(6.0); 
     cout << "Length of line : " << line.getLength() <<endl;
   
     // 不使用成员函数设置长度⭐️
     line.length = 10.0; // OK: 因为 length 是公有的
     cout << "Length of line : " << line.length <<endl;
     return 0;
  }
  //运行结果
  Length of line : 6
  Length of line : 10
  ```

- 私有（private)成员

  **私有**成员变量或函数在类的外部是不可访问的，甚至是不可查看的。**只有类和友元函数可以访问私有成员。**

  默认情况下，类的所有成员都是私有的。例如在下面的类中，**width** 是一个私有成员，这意味着，如果您没有使用任何访问修饰符，类的成员将被假定为私有成员：

  一个例子🌰：	

  ```C++
  class Box
  {
   double width;
   public:
      double length;
      void setWidth( double wid );
      double getWidth( void );
  };
  ```

  实际操作中，我们一般会在私有区域定义数据，然后在公有区域定义相关函数，以便类可以在外部调用这些函数用来获取以及修改类的私有变量及函数。

  ```C++
  #include <iostream>
   
  using namespace std;
   
  class Box
  {
     public:
        double length;
        void setWidth( double wid );
        double getWidth( void );
   
     private:
        double width;
  };
   
  // 成员函数定义
  double Box::getWidth(void)
  {
      return width ;
  }
   
  void Box::setWidth( double wid )
  {
      width = wid;
  }
   
  // 程序的主函数
  int main( )
  {
     Box box;
   
     // 不使用成员函数设置长度
     box.length = 10.0; // OK: 因为 length 是公有的
     cout << "Length of box : " << box.length <<endl;
   
     // 不使用成员函数设置宽度
     // box.width = 10.0; // Error: 因为 width 是私有的
     box.setWidth(10.0);  // 使用成员函数设置宽度
     cout << "Width of box : " << box.getWidth() <<endl;
   
     return 0;
  }
  ```

- 保护（protected）成员

  保护成员变量与私有成员很相似，但有一点不同的是，保护成员的参数可以通过类的派生类（子类）访问，而私有成员的则不可以。

  ```C++
  #include <iostream>
  using namespace std;
   
  class Box
  {
     protected:
        double width;
  };
   
  class SmallBox:Box // SmallBox 是派生类
  {
     public:
        void setSmallWidth( double wid );
        double getSmallWidth( void );
  };
   
  // 子类的成员函数
  double SmallBox::getSmallWidth(void)
  {
      return width ;
  }
   
  void SmallBox::setSmallWidth( double wid )
  {
      width = wid;
  }
   
  // 程序的主函数
  int main( )
  {
     SmallBox box;
   
     // 使用成员函数设置宽度
     box.setSmallWidth(5.0);
     cout << "Width of box : "<< box.getSmallWidth() << endl;
   
     return 0;
  }
  ```

  #### <a name="7">3、构造函数与析构函数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  **类的构造函数：**类的**构造函数**是类的一种特殊的成员函数，它会在每次创建类的新对象时执行。构造函数的名称与类的名称是完全相同的，并且不会返回任何类型，也不会返回 void。构造函数可用于为某些成员变量设置初始值。✅（在这里可以类比与python中的init函数

  ```C++
  #include <iostream>
   
  using namespace std;
   
  class Line
  {
     public:
        void setLength( double len );
        double getLength( void );
        Line();  // 这是构造函数
   
     private:
        double length;
  };
   
  // 成员函数定义，包括构造函数
  Line::Line(void)
  {
      cout << "Object is being created" << endl;
  }
   
  void Line::setLength( double len )
  {
      length = len;
  }
   
  double Line::getLength( void )
  {
      return length;
  }
  // 程序的主函数
  int main( )
  {
     Line line;
   
     // 设置长度
     line.setLength(6.0); 
     cout << "Length of line : " << line.getLength() <<endl;
   
     return 0;
  }
  //输出结果
  Object is being created
  Length of line : 6
  ```

  **带有参数的构造参数：**默认的构造函数没有任何参数，但如果需要，构造函数也可以带有参数。这样在创建对象时就会给对象赋初始值，如下面的例子所示:（✅：就可以当成带有参数的init函数，在初始化的时候需要带参数使用）

  ```C++
  #include <iostream>
   
  using namespace std;
   
  class Line
  {
     public:
        void setLength( double len );
        double getLength( void );
        Line(double len);  // 这是构造函数
   
     private:
        double length;
  };
   
  // 成员函数定义，包括构造函数
  Line::Line( double len)
  {
      cout << "Object is being created, length = " << len << endl;
      length = len;
  }
   
  void Line::setLength( double len )
  {
      length = len;
  }
   
  double Line::getLength( void )
  {
      return length;
  }
  // 程序的主函数
  int main( )
  {
     Line line(10.0);
   
     // 获取默认设置的长度
     cout << "Length of line : " << line.getLength() <<endl;
     // 再次设置长度
     line.setLength(6.0); 
     cout << "Length of line : " << line.getLength() <<endl;
   
     return 0;
  }
  
  ```

  **使用初始化列表来初始化字段**

  假设有一个类 C，具有多个字段 X、Y、Z 等需要进行初始化，同理地，您可以使用上面的语法，只需要在不同的字段使用逗号进行分隔，如下所示：

  ```C++
  C::C( double a, double b, double c): X(a), Y(b), Z(c)
  {
    ....
  }
  ```

  使用初始化列表来初始化字段：

  ```C++
  Line::Line( double len): length(len)
  {
      cout << "Object is being created, length = " << len << endl;
  }
  ```

  上面的语法等同于如下语法：

  ```C++
  Line::Line( double len)
  {
      cout << "Object is being created, length = " << len << endl;
      length = len;
  }
  ```

  **类的析构函数**（作用于类的构造函数刚好相反）：类的**析构函数**是类的一种特殊的成员函数，它会在**每次删除所创建的对象时执**行。析构函数的名称与类的名称是完全相同的，只是在前面加了个波浪号（~）作为前缀，它不会返回任何值，也不能带有任何参数。**析构函数有助于在跳出程序（比如关闭文件、释放内存等）前释放资源。**

  ```C++
  #include <iostream>
   
  using namespace std;
   
  class Line
  {
     public:
        void setLength( double len );
        double getLength( void );
        Line();   // 这是构造函数声明
        ~Line();  // 这是析构函数声明
   
     private:
        double length;
  };
   
  // 成员函数定义，包括构造函数
  Line::Line(void)
  {
      cout << "Object is being created" << endl;
  }
  Line::~Line(void)
  {
      cout << "Object is being deleted" << endl;
  }
   
  void Line::setLength( double len )
  {
      length = len;
  }
   
  double Line::getLength( void )
  {
      return length;
  }
  // 程序的主函数
  int main( )
  {
     Line line;
   
     // 设置长度
     line.setLength(6.0); 
     cout << "Length of line : " << line.getLength() <<endl;
   
     return 0;
  }
  //输出结果
  Object is being created
  Length of line : 6
  Object is being deleted
  
  ```

  #### <a name="8">3、C++拷贝构造函数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  问题？(O_O)?  什么是拷贝构造函数？？？？

  首先对于普通类型的对象来说，它们之间的复制是很简单的，例如：

  ```cpp
  int a = 100;
  int b = a; 
  ```

  类的乱七八糟看不懂，跳过回头填坑

  #### <a name="9">4、C++友元函数(相当于给开后门，给某些函数特定权利可以访问私有资源)</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  **类的友元函数是定义在类外部，但有权访问类的所有私有（private）成员和保护（protected）成员。**尽管友元函数的原型有在类的定义中出现过，但是友元函数并不是成员函数。

  友元可以是一个函数，该函数被称为友元函数；友元也可以是一个类，该类被称为友元类，在这种情况下，整个类及其所有成员都是友元。

  ==如果要声明函数为一个类的友元，需要在类定义中该函数原型前使用关键字 **friend**，如下所示：==

  ```cpp
  class Box
  {
     double width;
  public:
     double length;
     friend void printWidth( Box box );
     void setWidth( double wid );
  };
  //同样的，声明类ClassTwo的所有成员函数作为类ClassOne的友元，需要在类ClassOne的定义中放置如下声明：
  friend class ClassTwo;
  ```

  ```cpp
  #include <iostream>
   
  using namespace std;
   
  class Box
  {
     double width;
  public:
     friend void printWidth( Box box );
     void setWidth( double wid );
  };
  
  // 成员函数定义
  void Box::setWidth( double wid )
  {
      width = wid;
  }
  
  // 请注意：printWidth() 不是任何类的成员函数
  void printWidth( Box box )
  {
     /* 因为 printWidth() 是 Box 的友元，它可以直接访问该类的任何成员 */
     cout << "Width of box : " << box.width <<endl;
  }
   
  // 程序的主函数
  int main( )
  {
     Box box;
   
     // 使用成员函数设置宽度
     box.setWidth(10.0);
     
     // 使用友元函数输出宽度
     printWidth( box );
   
     return 0;
  }
  
  ```

  #### <a name="10">5、内联函数</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  一般的函数有一个潜在的缺点：调用函数比求解等价表达式要慢得多。在大多数的机器上，调用函数都要做很多工作：调用前要先保存寄存器，并在返回时恢复，复制实参，程序还必须转向一个新位置执行。

  在C++中可以使用**内联函数，**其目的是为了提高函数的执行效率**，**通常与类一起使用。如果一个函数是内联的，那么在编译时，编译器会把该函数的代码副本放置在每个调用该函数的地方。

  对内联函数进行任何修改，都需要重新编译函数的所有客户端，因为编译器需要重新更换一次所有的代码，否则将会继续使用旧的函数。

  如果想把一个函数定义为内联函数，则需要在函数名前面放置关键字 **inline**，在调用函数之前需要对函数进行定义。如果已定义的函数多于一行，编译器会忽略 inline 限定符。

  在类定义中的定义的函数都是内联函数，即使没有使用 **inline** 说明符。

  下面是使用内联函数来返回两个数中的最大值：

  ```cpp
  #include <iostream>
  using namespace std;
  
  inline int Max(int x, int y)
  {
     return (x > y)? x : y;
  }
  
  // 程序的主函数
  int main( )
  {
  
     cout << "Max (20,10): " << Max(20,10) << endl;
     cout << "Max (0,200): " << Max(0,200) << endl;
     cout << "Max (100,1010): " << Max(100,1010) << endl;
     return 0;
  }
  //输出结果
  Max (20,10): 20
  Max (0,200): 200
  Max (100,1010): 1010
  ```

  有了内联函数，就能像调用一个函数那样方便地重复使用一段代码，而不需要付出执行函数调用的额外开销。很显然，使用内联函数会是最终可执行程序的体积增加。以空间换取时间，或消耗时间来增加空间，这是计算机学科中常用的方法。

  内联函数中的代码应该只是很简单、执行很快的几条语句。如果一个函数较为复杂，它执行的时间可能上万倍于函数调用的额外开销，那么将其作为内联函数处理的结果是付出让代码体积增加不少的代价，却只使速度提高了万分之一，这显然是不划算的，而且有些函数即使声明为内联的也不一定会被编译器内联。

  有时函数看上去很简单，例如只有一个包含一两条语句的循环，但该循环的执行次数可能很多，要消耗大量时间，那么这种情况也不适合将其实现为内联函数。

  另外需要注意的是，调用内联函数的语句前必须已经出现内联函数的定义（即整个函数体），而不能只出现内联函数的声明。

  ✅：**也就是说内敛函数相当于是对传统函数的改造，在定义时需要在其开头位置添加inline符号，该类函数在执行过程中相当于不需要像传统函数使用时老需要寄存调用，直接将代码复制到各个需要调用的地方**

  #### <a name="11">6、C++ this指针</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  在 C++ 中，每一个对象都能通过 **this** 指针来访问自己的地址。**this** 指针是所有成员函数的隐含参数。因此，在成员函数内部，它可以用来指向调用对象。

  友元函数没有 **this** 指针，因为友元不是类的成员。只有成员函数才有 **this** 指针。

  ```cpp
  #include <iostream>
   
  using namespace std;
  
  class Box
  {
     public:
        // 构造函数定义
        Box(double l=2.0, double b=2.0, double h=2.0)
        {
           cout <<"Constructor called." << endl;
           length = l;
           breadth = b;
           height = h;
        }
        double Volume()
        {
           return length * breadth * height;
        }
        int compare(Box box)
        {
           return this->Volume() > box.Volume();//这个地方的this就是指向的Box这个类的本身
        }
     private:
        double length;     // Length of a box
        double breadth;    // Breadth of a box
        double height;     // Height of a box
  };
  
  int main(void)
  {
     Box Box1(3.3, 1.2, 1.5);    // Declare box1
     Box Box2(8.5, 6.0, 2.0);    // Declare box2
  
     if(Box1.compare(Box2))
     {
        cout << "Box2 is smaller than Box1" <<endl;
     }
     else
     {
        cout << "Box2 is equal to or larger than Box1" <<endl;
     }
     return 0;
  }
  //输出结果
  Constructor called.
  Constructor called.
  Box2 is equal to or larger than Box1
  ```

  #### <a name="12">7、指向类的指针</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  一个指向 C++ 类的指针与指向结构的指针类似，访问指向类的指针的成员，需要使用成员访问运算符 **->**，就像访问指向结构的指针一样。与所有的指针一样，您必须在使用指针之前，对指针进行初始化。

  ```CPP
  #include <iostream>
   
  using namespace std;
  
  class Box
  {
     public:
        // 构造函数定义
        Box(double l=2.0, double b=2.0, double h=2.0)
        {
           cout <<"Constructor called." << endl;
           length = l;
           breadth = b;
           height = h;
        }
        double Volume()
        {
           return length * breadth * height;
        }
     private:
        double length;     // Length of a box
        double breadth;    // Breadth of a box
        double height;     // Height of a box
  };
  
  int main(void)
  {
     Box Box1(3.3, 1.2, 1.5);    // Declare box1
     Box Box2(8.5, 6.0, 2.0);    // Declare box2
     Box *ptrBox;                // Declare pointer to a class.
  
     // 保存第一个对象的地址
     ptrBox = &Box1;
  
     // 现在尝试使用成员访问运算符来访问成员
     cout << "Volume of Box1: " << ptrBox->Volume() << endl;
  
     // 保存第二个对象的地址
     ptrBox = &Box2;
  
     // 现在尝试使用成员访问运算符来访问成员
     cout << "Volume of Box2: " << ptrBox->Volume() << endl;
    
     return 0;
  }
  //输出结果
  Constructor called.
  Constructor called.
  Volume of Box1: 5.94
  Volume of Box2: 102
  ```

  #### <a name="13">8、C++类的静态成员</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  我们可以使用 **static** 关键字来把类成员定义为静态的。当我们声明类的成员为静态时，这意味着无论创建多少个类的对象，静态成员都只有一个副本。

  **静态成员在类的所有对象中是共享的。如果不存在其他的初始化语句，在创建第一个对象时，所有的静态数据都会被初始化为零**。我们不能把静态成员放置在类的定义中，但是可以在类的外部通过使用==范围解析运算符 **::** 来重新声明静态变量==从而对它进行初始化，如下面的实例所示。

  下面的实例有助于更好地理解静态数据成员的概念：

  ```cpp
  #include <iostream>
   
  using namespace std;
  
  class Box
  {
     public:
        static int objectCount;
        // 构造函数定义
        Box(double l=2.0, double b=2.0, double h=2.0)
        {
           cout <<"Constructor called." << endl;
           length = l;
           breadth = b;
           height = h;
           // 每次创建对象时增加 1
           objectCount++;
        }
        double Volume()
        {
           return length * breadth * height;
        }
     private:
        double length;     // 长度
        double breadth;    // 宽度
        double height;     // 高度
  };
  
  // 初始化类 Box 的静态成员
  int Box::objectCount = 0;
  ‼️‼️ //在访问这种静态参数时，这里的访问符号不再是. 而是变成了::
  int main(void)
  {
     Box Box1(3.3, 1.2, 1.5);    // 声明 box1
     Box Box2(8.5, 6.0, 2.0);    // 声明 box2
  
     // 输出对象的总数
     cout << "Total objects: " << Box::objectCount << endl;
  
     return 0;
  }
  //输出结果
  Constructor called.
  Constructor called.
  Total objects: 2
  //这里static的意思就是不管怎么搞，怎么实例化，大家各个实例之间都是用同一个参数，也就是说他不属于任何一个特定的个体实例化，而是级别更高直属于类本身的，所以访问符号也从.变为了::
  ```

  #### <a name="14">9、静态函数成员</a><a style="float:right;text-decoration:none;" href="#index">[Top]</a>

  如果把函数成员声明为静态的，就可以把函数与类的任何特定对象独立开来。静态成员函数即使在类对象不存在的情况下也能被调用，**静态函数**只要使用类名加范围解析运算符 **::** 就可以访问。

  静态成员函数只能访问静态数据成员，不能访问其他静态成员函数和类外部的其他函数。

  静态成员函数有一个类范围，他们不能访问类的 this 指针。您可以使用静态成员函数来判断类的某些对象是否已被创建。

  ```cpp
  #include <iostream>
   
  using namespace std;
  
  class Box
  {
     public:
        static int objectCount;
        // 构造函数定义
        Box(double l=2.0, double b=2.0, double h=2.0)
        {
           cout <<"Constructor called." << endl;
           length = l;
           breadth = b;
           height = h;
           // 每次创建对象时增加 1
           objectCount++;
        }
        double Volume()
        {
           return length * breadth * height;
        }
        static int getCount()
        {
           return objectCount;
        }
     private:
        double length;     // 长度
        double breadth;    // 宽度
        double height;     // 高度
  };
  
  // 初始化类 Box 的静态成员
  int Box::objectCount = 0;
  
  int main(void)
  {
    
    
    ‼️‼️ //注意，这种静态参数（变量及函数）的调用需要使用::而不是跟以往一样使用的是单点号，这里需要注意
      
      
     // 在创建对象之前输出对象的总数
     cout << "Inital Stage Count: " << Box::getCount() << endl;
  
     Box Box1(3.3, 1.2, 1.5);    // 声明 box1
     Box Box2(8.5, 6.0, 2.0);    // 声明 box2
  
     // 在创建对象之后输出对象的总数
     cout << "Final Stage Count: " << Box::getCount() << endl;
  
     return 0;
  }
  //输出结果
  Inital Stage Count: 0
  Constructor called.
  Constructor called.
  Final Stage Count: 2
  ```

  