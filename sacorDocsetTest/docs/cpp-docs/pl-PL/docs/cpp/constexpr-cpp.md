---
title: constexpr (C++)
ms.date: 04/06/2018
f1_keywords:
  - constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
---
# <a name="constexpr-c"></a>constexpr (C++)

Słowo kluczowe **constexpr** został wprowadzony w C ++ 11 i ulepszone w języku C ++ 14. Oznacza to, *wyrażenie stałe*. Podobnie jak **const**, można go zastosować do zmiennych, aby błąd kompilatora jest wywoływane, jeśli dowolny kod próbuje zmodyfikować wartość. W odróżnieniu od **const**, **constexpr** również będą stosowane do funkcji i klasy konstruktorów. **wyrażenia constexpr** wskazuje, że wartość lub wartość zwracana jest stała i, jeśli to możliwe, jest obliczana w czasie kompilacji.

A **constexpr** wartości całkowitej może służyć wszędzie tam, gdzie stała liczba całkowita jest wymagany, takie jak argumentów szablonu i deklaracje tablicy. A gdy wartość może zostać obliczony w czasie kompilacji, zamiast w czasie wykonywania, może ono pomóc program działają szybciej i używanie mniejszej ilości pamięci.

Aby ograniczyć złożoność obliczeń stałą czasu kompilacji oraz ich potencjalny wpływ na czas kompilacji, C ++ 14 standardowa wymaga typy w wyrażeniach stałych jako [typy literałów](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Składnia

> **wyrażenia constexpr** *typem literału* *identyfikator* ** = ** *wyrażenie_stałe* **;** 
>  **constexpr** *typem literału* *identyfikator* **{** *wyrażenia stałego * **}** **;** 
>  **constexpr** *typem literału* *identyfikator* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parametry

*params*<br/>
Jeden lub więcej parametrów, z których każdy musi być typem literału więc musi sam być wyrażeniem stałym.

## <a name="return-value"></a>Wartość zwracana

Zmienna constexpr lub funkcja musi zwracać [literalne](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>zmienne constexpr

Główną różnicą między const i zmienne constexpr jest, że Inicjalizacja stałych zmiennej może zostać odroczony do czasu wykonywania. Zmienna constexpr musi zostać zainicjowany w czasie kompilacji.  Wszystkie zmienne wyrażeń constexpr są const.

- Zmienna może być zadeklarowany z **constexpr**, jeśli jest typem literału, a został zainicjowany. Jeśli inicjalizacja jest wykonywana przez konstruktora, Konstruktor musi być zadeklarowany jako **constexpr**.

- Odwołanie może być zadeklarowany jako constexpr, jeśli obiekt, który odwołuje się do został zainicjowany przez wyrażenie stałe i konwersje niejawne, które są wywoływane podczas inicjowania są również wyrażeń stałych.

- Wszystkie deklaracje **constexpr** musi być zmienną lub funkcję **constexpr** specyfikator.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> funkcjach ze specyfikatorem constexpr

A **constexpr** funkcji jest jednym którego zwracana wartość może zostać obliczony w czasie kompilacji podczas używania kodu wymaga. Korzystanie z kodu wymaga wartości zwracanej w czasie kompilacji, na przykład zainicjować **constexpr** zmiennej lub podaj argument szablonu bez typu. Jeśli argumenty mają **constexpr** wartości **constexpr** funkcja daje stałą czasu kompilacji. Gdy zostanie wywołana z non -**constexpr** argumentów, lub gdy jego wartość nie jest wymagane w czasie kompilacji, generuje wartość w czasie wykonywania, jak normalne działanie. (To zachowanie podwójną pozwala uniknąć do zapisania **constexpr** i innych niż-**constexpr** wersji tej samej funkcji.)

A **constexpr** funkcji ani konstruktora jest niejawnie **wbudowane**.

Do funkcji constexpr stosowane następujące reguły:

- A **constexpr** funkcja musi akceptować i zwracać tylko [typy literałów](trivial-standard-layout-and-pod-types.md#literal_types).

- A **constexpr** funkcji mogą być cykliczne.

- Nie można go [wirtualnego](../cpp/virtual-cpp.md). Nie można zdefiniować Konstruktor jako constexpr, jeśli wszystkie wirtualne klasy bazowe otaczającej klasy.

- Treść mogą być definiowane jako `= default` lub `= delete`.

- Nie może zawierać treści **goto** instrukcje lub bloki try.

- Jawna specjalizacja szablonu-constexpr mogą być deklarowane jako **constexpr**:

- Jawna specjalizacja **constexpr** szablonu nie musi być również **constexpr**:

Następujące reguły mają zastosowanie do **constexpr** funkcji w programie Visual Studio 2017 i nowszych:

- Może on zawierać **Jeśli** i **Przełącz** instrukcji i wszystkie instrukcje pętli, tym **dla**, na podstawie zakresu, **podczas**i **czy — gdy**.

- Może ona zawierać deklaracje zmiennych lokalnych, ale zmienna musi zostać zainicjowany, musi być typem literału i nie może być statyczne lub lokalnej wątku. Lokalnie zadeklarowanej zmiennej nie musi być wartością stałą i może mutować.

- Funkcja constexpr niestatycznego elementu członkowskiego nie musi być niejawnie const.

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> W debugerze programu Visual Studio podczas debugowania, bez zoptymalizowana debugowanie kompilacji, można stwierdzić czy **constexpr** funkcja jest oceniana w czasie kompilacji, umieszczając znajdującym się w nim punkt przerwania. Jeśli punkt przerwania zostanie osiągnięty, funkcja została wywołana w czasie wykonywania.  Jeśli nie, następnie funkcja została wywołana w czasie kompilacji.

## <a name="extern-constexpr"></a>extern constexpr

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md) — opcja kompilatora powoduje, że kompilator zastosować [powiązania zewnętrzne](../c-language/external-linkage.md) do zmiennych zadeklarowanych za pomocą **extern constexpr**. We wcześniejszych wersjach programu Visual Studio i domyślnie lub jeśli **/Zc:externConstexpr-** jest określony, program Visual Studio stosuje zewnętrzne do **constexpr** nawet wtedy, gdy zmienne **extern** słowo kluczowe jest używane. **/Zc: externconstexpr** opcja jest dostępna, począwszy od wersji 15.6 programu Visual Studio 2017 Update. i jest domyślnie wyłączona. /Permissive-option nie włączać/Zc: externconstexpr.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono **constexpr** zmienne, funkcje i typ zdefiniowany przez użytkownika. W ostatniej instrukcji w funkcji main() **constexpr** funkcja elementu członkowskiego GetValue() to wywołanie czasu wykonywania, ponieważ wartość nie jest wymagane, żeby Cię widziano w czasie kompilacji.

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

## <a name="requirements"></a>Wymagania

Visual Studio 2015

## <a name="see-also"></a>Zobacz także

[Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)<br/>
[const](../cpp/const-cpp.md)
