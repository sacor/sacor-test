---
title: 標準轉換
ms.date: 11/19/2018
helpviewer_keywords:
  - 'standard conversions, categories of'
  - 'L-values [C++]'
  - 'conversions, standard'
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
---
# <a name="standard-conversions"></a>標準轉換

C++ 語言定義其基本類型之間的轉換。 同時定義指標、參考及成員指標衍生類型的轉換。 這些轉換稱為*標準轉換*。

本節將討論下列標準轉換：

- 整數提升

- 整數轉換

- 浮動轉換

- 浮動和整數轉換

- 算術轉換

- 指標轉換

- 參考轉換

- 成員指標轉換

    > [!NOTE]
    >  使用者定義的類型可以自行指定其轉換。 使用者定義型別轉換涵蓋[建構函式](../cpp/constructors-cpp.md)並[轉換](../cpp/user-defined-type-conversions-cpp.md)。

下列程式碼會引發轉換 (本範例是整數提升)：

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

必須產生參考類型，轉換結果才會是左值。 例如，使用者定義的轉換宣告為`operator int&()`傳回的參考，而且是左值。 不過，轉換宣告為`operator int()`傳回物件，並不是左值。

## <a name="integral-promotions"></a>整數提升

整數類資料類型的物件可以轉換成另一種範圍更廣的整數類資料類型 (也就是可代表一組更大範圍值的類型)。 這種擴展的轉換類型稱為「整數提升」。 整數提升可在能夠使用另一種整數類資料類型時，讓您在運算式中使用下列項目：

- 物件、 常值和類型的常數**char**和**short int**

- 列舉類型

- **int**位元欄位

- 列舉程式

C++ 提升為「保留值」。 也就是說，保證提升後的值會和提升之前的值一樣。 在保留值的提升，較短的整數類資料類型的物件 (例如位元欄位或類型的物件**char**) 升至類型**int**如果**int**可以代表完整原始類型的範圍。 如果**int**無法代表值的完整範圍，則物件會提升為類型**不帶正負號的 int**。雖然這種策略與 ANSI C 所使用的策略相同，但是保留值的轉換不會保留物件的正負號狀態。

保留值的提升和保留正負號狀態的提升通常會產生相同的結果。 不過，如果提升的物件是下列其中一項，則兩者可能會產生不同的結果：

- 運算元 **/** ， `%`， `/=`， `%=`， **<** ， **\< =** ， **>** ，或 **>=**

   這些運算子需要依據正負號判斷結果。 因此，保留值和保留正負號的提升套用至這些運算元時，會產生不同的結果。

- 左的運算元 **>>** 或 **>>=**

   執行移位作業時，這些運算子會將帶正負號和不帶正負號的數量視為不同。 對於帶正負號的數量，將數量右移會造成正負號位元傳播至空出的位元位置。 對於不帶正負號的數量，空出的位元位置會以零填滿。

- 多載函式的引數，或是依據運算元類型的正負號狀態進行引數比對的多載運算子之運算元  (請參閱[多載運算子](../cpp/operator-overloading.md)如需定義多載運算子。)

## <a name="integral-conversions"></a>整數轉換

整數轉換是在整數類資料類型之間執行。 整數類資料類型**char**， **int**，並**長**(和**簡短**，**簽署**，與**不帶正負號**一種類型的版本)。

**不帶正負號到帶正負號**

帶正負號整數類型的物件可以轉換成對應的不帶正負號的類型。 當這些轉換發生時，實際的位元模式不會改變，不過資料的解譯會改變。 請參考下列程式碼：

```cpp
#include <iostream>

using namespace std;
int main()
{
    short  i = -3;
    unsigned short u;

    cout << (u = i) << "\n";
}
// Output: 65533
```

在上述範例中，**帶正負號短**， `i`、 定義和初始化為負數的數字。 運算式`(u = i)`會導致`i`轉換成**unsigned short**再指派給`u`。

**不帶正負號到帶正負號**

不帶正負號整數類資料類型的物件可以轉換成對應的帶正負號資料類型。 不過，如果不帶正負號的物件的值超出可由帶正負號類型表示的範圍，這種轉換可能會造成資料的錯譯，如下列範例所示：

```cpp
#include <iostream>

using namespace std;
int main()
{
short  i;
unsigned short u = 65533;

cout << (i = u) << "\n";
}
//Output: -3
```

在上述範例中，`u`已**unsigned short**必須轉換成帶正負號的數量，以評估運算式的整數物件`(i = u)`。 因為在無法正確表示其值**帶正負號短**，資料會誤譯，如所示。

## <a name="floating-point-conversions"></a>浮點轉換

浮動類型的物件可以安全地轉換為更精確的浮動類型，也就是說，轉換時不會遺失精確度。 比方說，從不**浮點數**來**double**或從**double**來**長雙精度**是安全的而且值是不變。

如果其範圍可由該類型表示，則浮動類型的物件可以轉換為較不精確的類型。 (請參閱[浮動限制](../cpp/floating-limits.md)是浮動類型的範圍。)如果無法精確地表示原始值，可以將它轉換為下一個較高或下一個較小的可表示值。 如果這個值不存在，則結果會是未定義。 參考下列範例：

```cpp
cout << (float)1E300 << endl;
```

依類型可顯示的最大值**浮點數**是 3.402823466E38 — 更小的數值比 1E300。 因此，數值會轉換為無限，而且結果會是"inf"。

## <a name="conversions-between-integral-and-floating-point-types"></a>整數與浮點類型之間的轉換

某些運算式可能會導致浮點類型的物件轉換成整數類型，反之亦然。 當整數類資料類型的物件轉換成浮點類型，且原始值無法正確表示時，結果會是下一個較大或較小的可顯示值。

當浮動類型的物件轉換為整數類資料類型時，會將小數部分截斷。 在轉換過程中不會進行四捨五入。 截斷表示像 1.3 會轉換成 1，而-1.3 的數字會轉換為-1。

## <a name="arithmetic-conversions"></a>算術轉換

許多二元運算子 (所述[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)) 會造成運算元的轉換，並產生結果相同的方式。 導致這些運算子進行轉換的方式稱為「一般算術轉換」。 針對不同原生類型的運算元執行算術轉換如下表所示。 Typedef 類型是根據其基礎原生類型而運作。

### <a name="conditions-for-type-conversion"></a>類型轉換的條件

|符合條件|轉換|
|--------------------|----------------|
|任一個運算元為類型**長雙精度**。|另一個運算元會轉換成類型**長雙精度**。|
|上述不符合條件，且任一個運算元的類型是**double**。|另一個運算元會轉換成類型**double**。|
|上述條件不符合，且任一個運算元的類型是**浮點數**。|另一個運算元會轉換成類型**浮點數**。|
|不符合上述條件 (所有運算元都不是浮動類型)。|在運算元上執行整數提升如下：<br /><br />-如果任一個運算元的類型**unsigned long**，另一個運算元轉換為類型**unsigned long**。<br />-如果不符合上述條件，而且任一個運算元的型別**長**和其他型別的**不帶正負號的 int**，這兩個運算元都轉換成輸入**不帶正負號長**。<br />-如果不符合前述兩項條件，而且任一個運算元的型別**長**，另一個運算元轉換為類型**長**。<br />-如果不符合上述三個條件，而且任一個運算元的型別**不帶正負號的 int**，另一個運算元轉換為類型**不帶正負號的 int**。<br />-如果上述條件均符合，這兩個運算元都轉換成類型**int**。|

下列程式碼說明表格中所述的這些轉換規則：

```cpp
double dVal;
float fVal;
int iVal;
unsigned long ulVal;

int main() {
   // iVal converted to unsigned long
   // result of multiplication converted to double
   dVal = iVal * ulVal;

   // ulVal converted to float
   // result of addition converted to double
   dVal = ulVal + fVal;
}
```

在上述範例中的第一個陳述式會顯示兩個整數類資料類型 (`iVal` 和 `ulVal`) 的乘法。 符合的條件是兩個運算元是浮動類型，和一個運算元為類型**不帶正負號的 int**。因此，其他運算元`iVal`，轉換為類型**不帶正負號的 int**。此結果會指派給 `dVal`。 符合的條件是其中一個運算元的型別**雙精度浮點**; 因此，**不帶正負號的 int**相乘的結果轉換為類型**double**。

在上述範例中的第二個陳述式會顯示新增**浮點數**整數型別，並`fVal`和`ulVal`。 `ulVal`變數會轉換成類型**float** （資料表中的第三個條件）。 相加的結果會轉換成類型**雙**（第二個資料表中的條件） 並指派給`dVal`。

## <a name="pointer-conversions"></a>指標轉換

在執行指派、初始化、比較和其他運算式時，可以轉換指標。

### <a name="pointer-to-classes"></a>類別的指標

在兩種情況下，類別的指標可以轉換成基底類別的指標。

第一種情況是可存取指定的基底類別，而且轉換明確。 (請參閱[多重基底類別](../cpp/multiple-base-classes.md)的模稜兩可的基底類別參考的詳細資訊。)

基底類別是否可存取，取決於衍生中所使用的繼承種類。 請參考下圖中說明的繼承。

![顯示基底的繼承圖形&#45;類別存取範圍](../cpp/media/vc38xa1.gif "繼承圖形，顯示基底&#45;類別存取範圍") <br/>
說明基底類別存取範圍的繼承圖表

下表說明圖中所示情況的基底類別存取範圍。

### <a name="base-class-accessibility"></a>基底類別存取範圍

|函式類型|衍生|從<br /><br /> B * 到 A\*合法？|
|----------------------|----------------|-------------------------------------------|
|外部 (非類別範圍) 函式|Private|否|
||Protected|否|
||Public|是|
|B 成員函式 (B 範圍中)|Private|是|
||Protected|是|
||Public|是|
|C 成員函式 (C 範圍中)|Private|否|
||Protected|是|
||Public|是|

類別指標可以轉換成基底類別指標的第二種情況，是使用明確類型轉換  (請參閱[明確類型轉換運算子](explicit-type-conversion-operator-parens.md)的明確類型轉換的詳細資訊。)

這類轉換的結果會是「子物件」指標，也就是物件中以基底類別完整描述的部分。

下列程式碼會定義兩種類別 `A` 和 `B`，其中 `B` 衍生自 `A` (如需有關繼承的詳細資訊，請參閱 <<c0> [ 衍生類別](../cpp/inheritance-cpp.md)。)然後它會定義 `bObject`、`B` 類型的物件，以及兩個指向物件的指標 (`pA` 和 `pB`)。

```cpp
// C2039 expected
class A
{
public:
    int AComponent;
    int AMemberFunc();
};

class B : public A
{
public:
    int BComponent;
    int BMemberFunc();
};
int main()
{
   B bObject;
   A *pA = &bObject;
   B *pB = &bObject;

   pA->AMemberFunc();   // OK in class A
   pB->AMemberFunc();   // OK: inherited from class A
   pA->BMemberFunc();   // Error: not in class A
}
```

`pA` 指標是 `A *` 類型，可以解譯為表示「`A` 類型物件的指標」。 成員`bObject``(`這類`BComponent`並`BMemberFunc`) 類型是唯一的`B`，因此無法透過存取`pA`。 `pA` 指標只允許存取 `A` 類別中定義的那些物件特性 (成員函式和資料)。

### <a name="pointer-to-function"></a>函式的指標

函式的指標可以轉換成類型`void *`，如果型別`void *`夠大，足以容納該指標。

### <a name="pointer-to-void"></a>void 的指標

類型的指標**void**可轉換成任何其他類型，但只能使用明確的類型轉換的指標 (不同於在 C 中)。 任何類型的指標可以隱含地轉換成類型的指標**void**。不完整的型別物件的指標可以轉換成指標**void** （隱含） 和回 （明確）。 這類轉換的結果等於原始指標的值。 若物件宣告後，沒有足夠的資訊可用來判斷其大小和基底類別，則會將該物件視為不完整。

不是任何物件的指標**const**或是**volatile**能夠隱含轉換成類型的指標`void *`。

### <a name="const-and-volatile-pointers"></a>const 和 volatile 指標

C++未提供從標準轉換**const**或**volatile**不是類型的型別**const**或**volatile**。 不過，使用明確類型轉型 (包括不安全的轉換) 即可指定任何類型的轉換。

> [!NOTE]
>  C++ 成員指標 (靜態成員指標除外) 不同於一般指標，而且沒有相同的標準轉換。 靜態成員的指標是一般指標，具有與一般指標相同的轉換。

### <a name="null-pointer-conversions"></a>null 指標轉換

判斷值為零的整數常數運算式，或轉換為指標型別的運算式會轉換成稱為「null 指標」的指標。 這個指標保證與任何有效物件或函式的指標不相等 (除了以物件為主的指標以外，這些指標可能會內含相同的位移，並且仍然指向不同的物件)。

在 c++11 [nullptr](../cpp/nullptr.md)類型應該是慣用的 C 樣式 null 指標。

### <a name="pointer-expression-conversions"></a>指標運算式轉換

具有陣列類型的任何運算式都可以轉換成相同類型的指標。 轉換的結果是第一個陣列元素的指標。 下列範例將示範這類轉換：

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

導致函式傳回特殊類型的運算式會轉換成傳回該類型之函式的指標，但下列情形例外：

- 運算式做為傳址運算子的運算元 ( **&** )。

- 運算式做為函式呼叫運算子的運算元。

## <a name="reference-conversions"></a>參考轉換

在下列情況下，類別的參考可以轉換成基底類別的參考：

- 存取指定的基底類別。

- 轉換不可以模稜兩可。 (請參閱[多重基底類別](../cpp/multiple-base-classes.md)的模稜兩可的基底類別參考的詳細資訊。)

轉換的結果是表示基底類別子物件的指標。

## <a name="pointer-to-member"></a>成員的指標

在執行指派、初始化、比較和其他運算式時，可以轉換類別成員的指標。 本節將描述下列成員指標的轉換：

## <a name="pointer-to-base-class-member"></a>基底類別成員的指標

當下列條件符合時，就可以將基底類別成員的指標轉換為從其衍生之類別成員的指標：

- 反向轉換 (即從衍生類別的指標轉換為基底類別指標) 是可以存取的。

- 衍生的類別無法由基底類別進行虛擬繼承。

當左運算元為成員的指標時，右運算元必須是成員指標類型，或者必須是判斷值為 0 的常數運算式。 這項指派只在下列情況下有效：

- 右運算元為與左運算元相同類別的成員指標。

- 左運算元是一種公開且明確地從右運算元類別所衍生的類別成員指標。

## <a name="integral-constant-conversions"></a>整數常數轉換

運算結果為零的整數常數運算式會轉換成「Null 指標」。 這個指標保證與任何有效物件或函式的指標不相等 (除了以物件為主的指標以外，這些指標可能會內含相同的位移，並且仍然指向不同的物件)。

下列程式碼說明在 `i` 類別中針對成員 `A` 所定義的指標。 指標 (即 `pai`) 已初始化為 0，為 Null 指標。

```cpp
class A
{
public:
int i;
};

int A::*pai = 0;

int main()
{
}
```

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)