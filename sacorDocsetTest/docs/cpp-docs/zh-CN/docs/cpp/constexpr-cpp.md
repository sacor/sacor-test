---
title: constexpr (C++)
ms.date: 04/06/2018
f1_keywords:
  - constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
---
# <a name="constexpr-c"></a>constexpr (C++)

关键字**constexpr**已在 C++ 11 中引入的以及在 C++ 14 中改进。 这意味着*常量表达式*。 像**const**，可以应用于变量，以便如果任何代码尝试修改的值将引发编译器错误。 与不同**const**， **constexpr**也应用于函数和类构造函数。 **constexpr**指示的值或返回值是常数，并且如果可能，在编译时计算。

一个**constexpr**整数值可用于任何 const 整数时必需的例如模板自变量和数组声明中。 和时可以在编译时，而不是运行时计算一个值，它可以帮助你更快地运行，并使用较少的内存的程序。

若要限制的编译时常量计算和它们在编译时的潜在影响的复杂性，标准 C + + 14，需要常量表达式中的类型为[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="syntax"></a>语法

> **constexpr** *文本类型* *标识符* **=** *常量表达式* **;** 
>  **constexpr** *文本类型* *标识符* **{** *常量表达式* **}** **;** 
>  **constexpr** *文本类型* *标识符* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>参数

*params*<br/>
一个或多个参数，其中每个必须是文本类型，并且其本身必须是常数表达式。

## <a name="return-value"></a>返回值

Constexpr 变量或函数必须返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

## <a name="constexpr-variables"></a>constexpr 变量

Const 和 constexpr 变量之间的主要区别是 const 变量的初始化可以延迟到运行时。 Constexpr 变量必须在编译时进行初始化。  所有 constexpr 变量均为常量。

- 可以使用声明的变量**constexpr**，如果它具有文本类型并且未被初始化。 如果由构造函数执行初始化，则构造函数必须声明为**constexpr**。

- 如果所引用的对象已由常数表达式初始化，并且在初始化期间所调用的任何隐式转换也均是常数表达式，则可能将引用声明为 constexpr。

- 所有声明**constexpr**变量或函数必须具有**constexpr**说明符。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> constexpr 函数

一个**constexpr**函数是一个可在何时使用代码需要它的编译时计算其返回值。 使用代码要求返回的值在编译时，例如，若要初始化**constexpr**变量或提供的非类型模板参数。 当其自变量都**constexpr**值， **constexpr**函数生成编译时常量。 使用非调用时**constexpr**自变量，或当它的值不需要在编译时，它生成的值在运行时与正则函数一样。 (此双重行为使你无需编写**constexpr**和非-**constexpr**相同函数的版本。)

一个**constexpr**函数或构造函数是隐式**内联**。

以下规则适用于 constexpr 函数：

- 一个**constexpr**函数必须接受并仅返回[文本类型](trivial-standard-layout-and-pod-types.md#literal_types)。

- 一个**constexpr**函数可以是递归。

- 它不能[虚拟](../cpp/virtual-cpp.md)。 如果在封闭类具有任何虚拟基类，构造函数不能定义为 constexpr。

- 主体可以定义为 `= default` 或 `= delete`。

- 不能包含正文**goto**语句或 try 块。

- 可以将非 constexpr 模板的显式专用化声明为**constexpr**:

- 显式专用化**constexpr**模板不需要也是**constexpr**:

以下规则适用于**constexpr**函数在 Visual Studio 2017 及更高版本：

- 它可能包含**如果**和**切换**语句以及所有循环语句，其中包括**有关**，基于范围的 for，**而**，和**执行操作-虽然**。

- 它可能包含局部变量声明，但该变量必须初始化，必须是文本类型，并且不能为静态或线程本地。 本地声明的变量不需要是常量，且可能会发生变化。

- Constexpr 非静态成员函数不需要为隐式 const。

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> 在 Visual Studio 调试器中，在调试非优化调试版本，您可以指示是否**constexpr**函数评估在编译时放置在其中一个断点。 如果命中该断点，则在运行时调用该函数。  如果未命中，则在编译时调用该函数。

## <a name="extern-constexpr"></a>extern constexpr

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md)编译器选项将使编译器要应用[外部链接](../c-language/external-linkage.md)到通过使用声明的变量**extern constexpr**。 在早期版本的 Visual Studio 中，并且默认情况下或者如果 **/Zc:externConstexpr-** 指定，则 Visual Studio 将应用到的内部链接**constexpr**变量，即使**extern**关键字使用。 **/Zc: externconstexpr**选项是从开始在 Visual Studio 2017 更新 15.6 版中提供。 和默认情况下处于关闭状态。 /Permissive-option 不会启用 /zc: externconstexpr。

## <a name="example"></a>示例

下面的示例演示**constexpr**变量、 函数和用户定义类型。 在 main （） 中的最后一个语句中**constexpr**成员函数 getvalue （） 是运行时调用，因为不需要在编译时已知的值。

```cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&ary)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n*fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue()
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;

}
```

## <a name="requirements"></a>要求

Visual Studio 2015

## <a name="see-also"></a>请参阅

[声明和定义](../cpp/declarations-and-definitions-cpp.md)<br/>
[const](../cpp/const-cpp.md)
