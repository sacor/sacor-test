---
title: constexpr (C++)
ms.date: 04/06/2018
f1_keywords:
  - constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
---
# <a name="constexpr-c"></a>constexpr (C++)

Das Schlüsselwort **"constexpr"** wurde in C ++ 11 eingeführt und in C ++ 14 verbessert. Es bedeutet, dass *Konstantenausdruck*. Wie **const**, sie können auf Variablen angewendet werden, sodass ein Compilerfehler ausgelöst wird, wenn der Code versucht wird, um den Wert ändern. Im Gegensatz zu **const**, **"constexpr"** kann auch auf Funktionen angewendet werden und Klassenkonstruktoren. **"constexpr"** gibt an, dass der Wert oder Rückgabewert, konstant ist und wenn möglich, zur Kompilierungszeit berechnet wird.

Ein **"constexpr"** ganzzahliger Wert kann verwendet werden, wenn eine ganzzahlige Konstante erforderlich, z. B. in Vorlagenargumenten und Arraydeklarationen ist. Und wenn Sie ein Wert zur Kompilierzeit statt zur Laufzeit berechnet werden kann, können sie Ihr Programm schneller ausgeführt und belegen weniger Speicher.

Um die Komplexität der Kompilierzeit konstanter Berechnungen und deren möglichen Auswirkungen auf den Zeitpunkt der Kompilierung zu beschränken, erfordert der C ++ 14-standard der Typen in Konstanten Ausdrücken sein [Literaltypen](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Syntax

> **"constexpr"** *Literal-Typ* *Bezeichner* ** = ** *Konstantenausdruck* **;** 
>  **"constexpr"** *Literal-Typ* *Bezeichner* **{** *konstanter Ausdruck * **}** **;** 
>  **"constexpr"** *Literal-Typ* *Bezeichner* **(** *Params* **)** **;** 
>  **"constexpr"** *"ctor"* **(** *Params* **)** **;**

## <a name="parameters"></a>Parameter

*params*<br/>
Ein oder mehrere Parameter, von die jeder ein literal-Typ sein muss, und muss selbst sein ein konstanter Ausdruck.

## <a name="return-value"></a>Rückgabewert

Eine Constexpr-Variable oder Funktion muss Zurückgeben einer [Literaltyp](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>constexpr-Variablen

Der Hauptunterschied zwischen const- und Constexpr-Variablen ist, dass die Initialisierung einer const-Variablen bis zur Laufzeit verzögert werden kann. Eine Constexpr-Variable muss zum Zeitpunkt der Kompilierung initialisiert werden.  Alle constexpr-Variablen sind auch const.

- Eine Variable kann mit deklariert werden **"constexpr"** , wenn sie über einen Literaltyp verfügt und initialisiert wird. Wenn die Initialisierung von einem Konstruktor ausgeführt wird, muss der Konstruktor deklariert werden, als **"constexpr"** .

- Ein Verweis kann als constexpr deklariert werden, wenn das Objekt, auf das er verweist, durch einen konstanten Ausdruck initialisiert wurde und alle impliziten Konvertierungen, die während der Initialisierung aufgerufen werden, auch konstante Ausdrücke sind.

- Alle Deklarationen einer **"constexpr"** Variable oder Funktion müssen die **"constexpr"** Spezifizierer.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a> Constexpr-Funktionen

Ein **"constexpr"** -Funktion ist eine, deren Rückgabewert zum Zeitpunkt der Kompilierung kann es beim Nutzen von Code müssen berechnet werden kann. Nutzen von Code erfordert den Rückgabewert zum Zeitpunkt der Kompilierung, z. B. zum Initialisieren einer **"constexpr"** Variable, oder geben Sie ein Nichttyp-Vorlagenargument. Wenn die Argumente sind **"constexpr"** Werte eine **"constexpr"** Funktion generiert eine Kompilierzeitkonstante. Bei einem Aufruf mit nicht- **"constexpr"** Argumente, oder wenn der Wert nicht zum Zeitpunkt der Kompilierung erforderlich ist, erzeugt es den Wert zur Laufzeit wie eine reguläre Funktion. (Dieses duale Verhalten erspart Ihnen schreiben **"constexpr"** und nicht- **"constexpr"** Versionen der gleichen Funktion.)

Ein **"constexpr"** -Funktion oder der Konstruktor ist implizit **Inline**.

Die folgenden Regeln gelten für Constexpr-Funktionen:

- Ein **"constexpr"** Funktion akzeptieren und zurückgeben, nur muss [Literaltypen](trivial-standard-layout-and-pod-types.md#literal_types).

- Ein **"constexpr"** -Funktion kann rekursiv sein.

- Ist nicht möglich [virtuellen](../cpp/virtual-cpp.md). Ein Konstruktor kann nicht als Constexpr definiert werden, wenn die einschließende Klasse über virtuellen Basisklassen verfügt.

- Der Text kann als `= default` oder `= delete` definiert werden.

- Der Text darf nicht **Goto** Anweisungen oder Try-Blöcken.

- Eine explizite Spezialisierung einer nicht-Constexpr-Vorlage kann deklariert werden, als **"constexpr"** :

- Eine explizite Spezialisierung einer **"constexpr"** Vorlage muss nicht auch **"constexpr"** :

Die folgenden Regeln gelten für **"constexpr"** Funktionen in Visual Studio 2017 und höher:

- Sie enthält eventuell **Wenn** und **wechseln** Anweisungen und alle schleifenanweisungen einschließlich **für**, bereichsbasierte for, **während**, und **sind – während**.

- Es kann Deklarationen von lokale Variable enthalten, aber die Variable muss initialisiert werden, muss ein literal-Typ sein und darf nicht statisch oder Thread-lokalen. Die lokal deklarierte Variable ist nicht erforderlich, "const" sein und möglicherweise geändert wird.

- Eine nicht statische Member-Funktion "constexpr" ist nicht erforderlich, um implizit const ist.

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> In Visual Studio-Debugger, Debuggen, eine nicht optimierte Debug-Build, Sie können erkennen, ob eine **"constexpr"** Funktion wird zum Zeitpunkt der Kompilierung ausgewertet wird, indem Sie einen Haltepunkt in die Datei einfügen. Wenn der Haltepunkt erreicht wird, wurde die Funktion zur Laufzeit aufgerufen.  Wenn dies nicht der Fall ist, wurde die Funktion zum Zeitpunkt der Kompilierung aufgerufen.

## <a name="extern-constexpr"></a>externe constexpr

Die [/Zc: externconstexpr](../build/reference/zc-externconstexpr.md) Compileroption veranlasst den Compiler anzuwendende [externe Verknüpfung](../c-language/external-linkage.md) Variablen deklariert, indem **externe Constexpr**. In früheren Versionen von Visual Studio, und standardmäßig oder wenn **/Zc:externConstexpr-** angegeben ist, wird Visual Studio wendet internen Verknüpfung, **"constexpr"** Variablen auch dann, wenn die **"extern"** -Schlüsselwort wird verwendet. Die **/Zc: externconstexpr** Option ist verfügbar in Visual Studio 2017 Update 15.6 ab. und ist standardmäßig deaktiviert. / Zc: externconstexpr aktiviert der PERMISSIVE nicht.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt **"constexpr"** Variablen, Funktionen und einen benutzerdefinierten Typ. In der letzten Anweisung in main() die **"constexpr"** Memberfunktion GetValue()"einen Aufruf zur Laufzeit ist, da der Wert nicht unbedingt zum Zeitpunkt der Kompilierung bekannt sein.

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

## <a name="requirements"></a>Anforderungen

Visual Studio 2015

## <a name="see-also"></a>Siehe auch

[Deklarationen und Definitionen](../cpp/declarations-and-definitions-cpp.md)<br/>
[const](../cpp/const-cpp.md)
