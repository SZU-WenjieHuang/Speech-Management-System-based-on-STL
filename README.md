# Speech-Management-System-based-on-STL

### 01 STL map
在C++的标准模板库(STL)中，std::map 和 std::multimap 默认是按照键(key)的升序进行排列的。这是因为它们内部使用红黑树这种数据结构来存储元素，红黑树是一种自平衡的二叉搜索树，本身就有序。

在声明 std::map 或 std::multimap 时，你可以选择提供一个自定义的比较函数或者函数对象（也称为仿函数），但这并非必须。如果你没有提供，那么就会使用默认的 std::less<Key> 作为比较函数，这就是为什么 map 和 multimap 默认是升序排列的原因。
```cpp
std::map<int, std::string> m; // 默认按键升序排列
std::map<int, std::string, std::greater<int>> m; // 按键降序排列
```
在上面的例子中，第一个 map 会默认使用 std::less<int> 作为比较函数，结果是按照键升序排列；第二个 map 则明确指定了 std::greater<int> 作为比较函数，结果是按照键降序排列。

### 02 ofstream::open
ofstream::open 是一个成员函数，用于打开一个文件以供写入（即输出）操作。它需要两个参数：第一个参数是文件的路径和名称，第二个参数是用于指定文件打开模式的标志。常见的文件打开模式的标识有：

ios::out：这个文件被打开以供写入。这是 ofstream::open 的默认模式，即使你不指定这个标志，文件也会被打开以供写入。

ios::app：这个标志意味着所有写入的数据都会被添加到文件的末尾，而不是覆盖文件原有的内容。这就是所谓的 "append" 模式。

ios::in：文件被打开以供读取。这通常用于 ifstream，它是用于读取文件的类。

ios::binary：文件以二进制模式被打开，而不是文本模式。

ios::trunc：如果文件已经存在，那么它的内容会被丢弃（即被截断为0长度）。如果你没有指定 ios::app 或 ios::in，那么 ios::out 会默认使用这个模式。

### 03 std::istream::putback 
std::istream::putback 是一个成员函数，用于将一个字符放回到输入流中。这个函数只接受一个参数，即要放回的字符。

在你提到的代码中，ifs.putback(ch); 的意思是，将刚刚从输入文件流 ifs 中读取的字符 ch 放回到 ifs 中。这样，下一次从 ifs 读取字符时，会再次读取到这个字符。

### 04 random_shuffle 洗牌
这段代码是 C++ 中的一段，std::random_shuffle 是一个被 C++ 标准库提供的函数，用于随机地重新排列指定范围内的元素。

在这个例子中，v1 是一个 std::vector<int> 类型的对象，v1.begin() 和 v1.end() 分别返回一个指向 v1 的第一个元素和最后一个元素之后的位置的迭代器。std::random_shuffle(v1.begin(), v1.end()) 这行代码会将 v1 中的所有元素进行随机排序。

这是一个非常有用的函数，可以用于很多需要随机洗牌的情况，比如在模拟游戏中洗牌，或者在机器学习中打乱数据集的顺序。

然而，需要注意的是，std::random_shuffle 在 C++17 中已被废弃，转而推荐使用 std::shuffle，因为 std::shuffle 提供了更好的随机性控制。以下是如何使用 std::shuffle 的示例：

```cpp
#include <random>
#include <algorithm>

std::random_device rd;
std::mt19937 g(rd());

std::shuffle(v1.begin(), v1.end(), g);
```

### 05 迭代器
在 C++ 中，迭代器是一种设计模式，它提供了一种方法来访问容器对象中的元素，而不需要暴露该对象的内部表示。迭代器的行为在很多方面都类似于指针。

你可以将迭代器视为容器的“智能指针”。需要解引用迭代器才能访问它所指向的元素。例如，假设 it 是一个指向 std::vector<int> 的迭代器，那么 *it 就会得到 it 所指向的整数。

举个例子： std::vector<int>::iterator it

std::vector<int>::iterator 是一个类型，表示一个迭代器，它指向 std::vector<int> 中的元素。这是因为不同的容器可能有不同类型的迭代器，所以你需要明确指定迭代器的类型。所以不能是iterator it 因为没有指定类型。

在cpp11之后可以是 auto it






