---
title: Azioni rapide | Microsoft Docs
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 22a6c84608f8955e3a751af4ee2b9fb113645590
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="quick-actions"></a>Azioni rapide

Le [azioni rapide](refactoring-code-generation-quick-actions.md#quick-actions) consentono di generare codice, effettuarne il refactoring o modificarlo in altro modo con facilità tramite un'unica azione. Sono disponibili azioni rapide per C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) e i file di codice Visual Basic. Alcune azioni sono specifiche per un linguaggio e altre si applicano a tutti i linguaggi. Le azioni rapide possono essere applicate tramite l'icona Lampadina ![Icona Lampadina piccola](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") o premendo **CTRL** + **.** quando il cursore si trova sulla riga di codice appropriata.

La lampadina viene visualizzata se è presente una sottolineatura ondulata rossa e in Visual Studio è disponibile un suggerimento per correggere l'errore. Ad esempio, se è presente un errore indicato da una sottolineatura rossa ondulata, verrà visualizzata una lampadina quando sono disponibili correzioni per tale errore. Nel caso in cui terze parti forniscano diagnostiche e suggerimenti personalizzati, ad esempio includendoli in SDK, per un qualsiasi linguaggio, le lampadine di Visual Studio si illumineranno sulla base di tali regole.

## <a name="to-see-a-light-bulb"></a>Per visualizzare una lampadina

1. In molti casi le lampadine vengono visualizzate spontaneamente quando si posiziona il puntatore del mouse su un errore oppure sul margine destro dell'editor, quando si sposta il cursore su una riga che contiene un errore. Quando è presente una sottolineatura ondulata rossa, è possibile passarvi sopra con il puntatore del mouse per visualizzare la lampadina. È anche possibile fare in modo che la lampadina venga visualizzata quando si usa il mouse o la tastiera per spostarsi nel punto della riga in cui si verifica l'errore.

1. Premere **CTRL** + **.** in un punto qualsiasi della riga per richiamare la lampadina e passare direttamente all'elenco delle correzioni potenziali.

   ![Lampadina con passaggio del mouse](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Per visualizzare le potenziali correzioni

Fare clic sulla freccia GIÙ o sul collegamento Mostra correzioni potenziali per visualizzare un elenco delle azioni rapide eseguibili automaticamente dalla lampadina.

![Lampadina espansa](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Azioni rapide comuni

Ecco alcune delle azioni rapide comuni applicabili sia a codice C# che a codice Visual Basic.
- [Azioni per risolvere errori](#fix)
- [Azioni per la rimozione di codice non necessario](#remove)
- [Azioni per l'aggiunta di codice mancante](#add)
- [Trasformazioni del codice](#transform)

### <a id="fix"></a> Azioni per risolvere errori

#### <a name="correct-misspelled-type"></a>Correggere un tipo con errori di ortografia
|  ID errore | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| CS0103, BC30002 | C# e Visual Basic | Visual Studio 2015 Update 2 |

Se si digita accidentalmente un tipo con errori di ortografia in Visual Studio, questa azione rapida consente di correggerlo automaticamente.  Questi elementi vengono visualizzati nel menu Lampadina come **"Modifica '*tipo con errore*' in '*tipo corretto*'**.  Ad esempio:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

#### <a name="resolve-git-merge-conflict"></a>Risolvere i conflitti di unione Git
|  ID errore | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| CS8300, BC37284  | C# e Visual Basic | Visual Studio 2017 versione 15.3 |

Queste azioni rapide consentono di risolvere conflitti di unione Git apportando una modifica che rimuove i marcatori e il codice in conflitto.  

```csharp
// Before     
private void MyMethod()
{
<<<<<<< HEAD
    if (true)
    {

    }
=======
    if (false)
    {

    }
>>>>>>> upstream
}

// Take changes from 'HEAD'

// After 
private void MyMethod()
{
    if (true)
    {

    }
}
```

#### <a name="make-method-synchronous"></a>Rendere sincrono un metodo
|  ID errore | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| CS1998, BC42356 | C# e Visual Basic | Visual Studio 2015 Update 2 |

Quando si usa la parola chiave `async` / `Async` su un metodo, si prevede che venga usata anche la parola chiave `await` / `Await` in un punto all'interno del metodo stesso.  Se tuttavia ciò non avviene, viene visualizzata un'azione rapida che consente di impostare il metodo come sincrono rimuovendo la parola chiave `async` / `Async` e modificando il tipo restituito.  Usare l'opzione **Imposta il metodo come sincrono** dal menu Azioni rapide.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

#### <a name="make-method-asynchronous"></a>Rendere asincrono un metodo
|  ID errore | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| CS4032, BC37057 | C# e Visual Basic | Visual Studio 2017 |

Quando si usa la parola chiave `await`/`Await` all'interno di un metodo, si prevede che il metodo stesso sia contrassegnato dalla parola chiave `async`/`Async`.  Se tuttavia ciò non avviene, viene visualizzata un'azione rapida che consente di impostare il metodo come asincrono.  Usare l'opzione **Rendi asincrono il metodo/Rendi asincrona la funzione** dal menu Azioni rapide.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a id="remove"></a> Azioni per la rimozione di codice non necessario

#### <a name="remove-unnecesary-usingsimports"></a>Rimuovi istruzioni using/Imports non necessarie

|  Linguaggi applicabili |  Versione supportata |
|  -------------------- | ----------------  |
|  C# e Visual Basic | Visual Studio 2015 RTW |

L'azione rapida **Rimuovi istruzioni using non necessarie/Rimuovi istruzioni Imports non necessarie** consente di rimuovere eventuali istruzioni `using` e `Import` dal file corrente.  Quando si seleziona questo elemento, le istruzioni Imports di spazi dei nomi non usate vengono rimosse immediatamente.

#### <a name="remove-unnecessary-cast"></a>Rimuovere un cast non necessario
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0004 | C# e Visual Basic | Visual Studio 2015 RTW |

Se si esegue il cast di un tipo a un altro tipo che non richiede un cast, l'azione rapida **Rimuovi cast non necessario** consente di rimuovere il cast dal codice.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```
```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

#### <a name="remove-unused-variables"></a>Rimuovere variabili non usate
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| CS0219, BC42024 | C# e Visual Basic | Visual Studio 2017 versione 15.3 |

Questa azione rapida consente di rimuovere le variabili dichiarate che non sono mai state usate nel codice.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

#### <a name="remove-type-from-default-value-expression"></a>Rimuovere il tipo dall'espressione con valore **predefinito**
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0034 | C# 7.1+ | Visual Studio 2017 versione 15.3 |

Questa azione rapida rimuove il tipo valore da un'espressione con valore predefinito e usa il [valore letterale `default`](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) quando il compilatore può dedurre il tipo dell'espressione.

```csharp 
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }

```

### <a id="add"></a> Azioni per l'aggiunta di codice mancante

#### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Aggiungere istruzioni using o Imports per i tipi in assembly di riferimento, pacchetti NuGet o altri tipi nella soluzione
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| CS0103, BC30451 | C# e Visual Basic| Visual Studio 2015 Update 2 |

Se si usano tipi situati in altri progetti della soluzione, l'azione rapida viene visualizzata automaticamente, ma gli altri devono essere abilitati da **Strumenti > Opzioni > C#** o nella scheda **Base > Avanzate**:  

* Suggerisci le direttive using/import per i tipi in assembly di riferimento
* Suggerisci le direttive using/import per i tipi in pacchetti NuGet

Dopo l'abilitazione, se si usa un tipo in uno spazio dei nomi non ancora importato, ma esistente in un assembly di riferimento o in un pacchetto NuGet, l'istruzione using/Imports viene creata.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

#### <a name="add-missing-casesdefault-caseboth"></a>Aggiungere elementi case mancanti, un'istruzione case predefinita o entrambi
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0010 | C# e Visual Basic| Visual Studio 2017 versione 15.3 |

Quando si crea un'istruzione `switch` in C# o un'istruzione `Select Case` in Visual Basic, è possibile usare un'azione codice per aggiungere automaticamente elementi case mancanti, un'istruzione case predefinita o entrambi.  Per un'istruzione vuota come la seguente:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

l'uso dell'azione rapida **Aggiungi entrambi** per inserire sia elementi case mancanti che un'istruzione case predefinita consente di creare quanto segue:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```
```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

#### <a name="add-null-checks-for-parameters"></a>Aggiungere controlli null per i parametri
| Linguaggi applicabili |  Versione supportata |
| -------------------- | ----------------  |
| C# e Visual Basic| Visual Studio 2017 versione 15.3 |

Questa azione rapida consente di aggiungere un controllo nel codice per indicare se un parametro è null.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

#### <a name="add-argument-name"></a>Aggiungi il nome di argomento
| Linguaggi applicabili |  Versione supportata |
| -------------------- | ----------------  |
| C# e Visual Basic| Visual Studio 2017 versione 15.3 |

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

#### <a name="add-braces"></a>Aggiungi parentesi graffe
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0011 | C# | Visual Studio 2017 RTW |

L'azione rapida Aggiungi parentesi graffe racchiude tra parentesi graffe le istruzioni `if` a riga singola.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true) 
{
    return "hello,world";
}
```

#### <a name="add-and-order-modifiers"></a>Aggiungi i modificatori e Ordina i modificatori
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0036 | C# e Visual Basic| Visual Studio 2017 versione 15.5 |
| IDE0040 | C# e Visual Basic| Visual Studio 2017 versione 15.5 |

Queste azioni rapide consentono di organizzare i modificatori grazie alla possibilità di ordinare i modificatori di accessibilità esistenti e di aggiungere quelli mancanti.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```
```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;

```

### <a id="transform"></a> Trasformazioni del codice

#### <a name="convert-if-construct-to-switch"></a>Convertire il costrutto **if** in **switch**
| Linguaggi applicabili |  Versione supportata |
| -------------------- | ----------------  |
| C# e Visual Basic| Visual Studio 2017 versione 15.3 |

Questa azione rapida consente di convertire un costrutto **if-then-else** in un costrutto **switch**.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

#### <a name="convert-to-interpolated-string"></a>Convertire in una stringa interpolata
| Linguaggi applicabili |  Versione supportata |
| -------------------- | ----------------  |
| C# 6.0+ e Visual Basic 14+ | Visual Studio 2017 RTW |

Le [stringhe interpolate](/dotnet/csharp/language-reference/keywords/interpolated-strings) rappresentano un modo semplice, simile al metodo **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)**, per esprimere stringhe con variabili incorporate.  Questa azione rapida riconosce i casi in cui le stringhe sono concatenate o usano **String.Format** e ne modifica l'utilizzo in quello di una stringa interpolata.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```
```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

#### <a name="use-object-initializers"></a>Usare gli inizializzatori di oggetto
| ID di diagnostica | Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0017 | C# e Visual Basic | Visual Studio 2017 RTW |

Questa azione rapida consente di usare gli [inizializzatori di oggetto](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) anziché richiamare il costruttore e introdurre righe aggiuntive di istruzioni di assegnazione.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```
```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

#### <a name="use-collection-initializers"></a>Usare gli inizializzatori di insieme
| ID di diagnostica | Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0028 | C# e Visual Basic | Visual Studio 2017 RTW |

Questa azione rapida consente di usare gli [inizializzatori di insieme](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) invece di più chiamate al metodo `Add` della classe.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```
```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}

```  

#### <a name="convert-auto-property-to-full-property"></a>Convertire una proprietà automatica in proprietà completa
|  Linguaggi applicabili |  Versione supportata |
|  -------------------- | ----------------  |
| C# e Visual Basic | Visual Studio 2017 versione 15.5 |

Questa azione rapida consente di convertire una proprietà automatica in una proprietà completa e viceversa.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; } 
}
```
```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property

```

#### <a name="convert-block-body-to-expression-bodied-member"></a>Convertire il corpo di blocco in membro con corpo di espressione
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 RTW |

Questa azione rapida consente di convertire i corpi di blocco in membri con corpo di espressione per metodi, costruttori, operatori, proprietà, indicizzatori e funzioni di accesso.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

#### <a name="convert-anonymous-function-to-local-function"></a>Convertire una funzione anonima in funzione locale
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0039 | C# 7.0+ | Visual Studio 2017 versione 15.5 |

Questa azione rapida converte le funzioni anonime in funzioni locali.

```csharp 
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

```

#### <a name="convert-referenceequals-to-is-null"></a>Convertire `ReferenceEquals` in `is null`
|  ID di diagnostica | Linguaggi applicabili |  Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0041 | C# 7.0+ | Visual Studio 2017 versione 15.5 |

Questa azione rapida suggerisce l'uso di [criteri di ricerca](/dotnet/csharp/pattern-matching) anziché del modello di codifica ```ReferenceEquals```, ove possibile.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

#### <a name="introduce-pattern-matching"></a>Introdurre criteri di ricerca
| ID di diagnostica | Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0020 | C# 7.0+ | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0+ | Visual Studio 2017 RTW |

Questa azione rapida suggerisce l'uso di [criteri di ricerca](/dotnet/csharp/pattern-matching) con cast e controlli null in C#.   

```csharp
// Before
if (o is int) 
{
    var i = (int)o; 
    ... 
}

// Use pattern matching

// After
if (o is int i) 
{
    ...
}

```
```csharp
// Before
var s = o as string;
if (s != null) 
{
    ...
}

// Use pattern matching

// After
if (o is string s) 
{
    ...
}
```

#### <a name="change-base-for-numeric-literals"></a>Modificare la base per i valori letterali numerici
| Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| C# 7.0+ e Visual Basic 14+ | Visual Studio 2017 versione 15.3 |

Questa azione rapida consente di convertire un valore letterale numerico da un sistema numerico di base a un altro. È possibile, ad esempio, convertire un numero in formato esadecimale o binario. 

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```
```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

#### <a name="insert-digit-separators-into-literals"></a>Inserire separatori di cifre in valori letterali
| Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| C# 7.0+ e Visual Basic 14+ | Visual Studio 2017 versione 15.3 |

Questa azione rapida consente di aggiungere caratteri separatori nei valori letterali.  

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```
```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

#### <a name="use-explicit-tuple-names"></a>Usare nomi di tupla espliciti
| ID di diagnostica | Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0033 | C# 7.0+ e Visual Basic 15+ | Visual Studio 2017 RTW |

Questa azione rapida identifica le aree in cui è possibile usare nomi di tupla espliciti invece di Elemento1, Elemento2 e così via.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```
```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

#### <a name="use-inferred-names"></a>Usare nomi dedotti
| ID di diagnostica | Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0037 | C# | Visual Studio 2017 versione 15.5 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 versione 15.5 |

Queste azioni rapide segnalano quando gli utenti possono usare nomi di membri dedotti nei tipi anonimi o usare i nomi di elementi di tuple dedotti di C# 7.1.

```csharp 
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```
```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);

```

#### <a name="deconstruct-tuple-declaration"></a>Decostruisci la dichiarazione di variabile
| ID di diagnostica | Linguaggi applicabili | Versione supportata |
| ------- | -------------------- | ----------------  |
| IDE0042 | C# 7.0+ | Visual Studio 2017 versione 15.5 |

Questa azione rapida consente di decostruire le dichiarazioni delle variabili di tupla. 

```csharp 
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

## <a name="see-also"></a>Vedere anche
* [Stili di codice e azioni rapide](code-styles-and-quick-actions.md)  
* [Scrittura e refactoring del codice (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
