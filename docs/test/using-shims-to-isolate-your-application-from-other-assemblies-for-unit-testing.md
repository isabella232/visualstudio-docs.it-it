---
title: Isolare l'app con sms (unit test)
description: Informazioni su come usare i tipi shim per deviare le chiamate a metodi specifici al codice scritto come parte del test. Uno shim può restituire risultati coerenti a ogni chiamata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 9bba159da05ad3e1c893c3fc241c44cd1c6de8d1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053976"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Usare gli sms per isolare l'app per gli unit test

**I tipi Shim** sono una delle due tecnologie che Microsoft Fakes Framework usa per isolare i componenti sotto test dall'ambiente. Gli shim deviano le chiamate ai metodi specifici al codice scritto come parte del test. Molti metodi restituiscono risultati diversi dipendenti dalle condizioni esterne, ma uno shim si trova sotto il controllo del test e può restituire risultati coerenti a ogni chiamata. In questo modo è più semplice scrivere i test.

Usare *s shims* per isolare il codice dagli assembly che non fanno parte della soluzione. Per isolare i componenti della soluzione l'uno dall'altro, usare *stub*.

Per una panoramica e indicazioni di "avvio rapido", vedere [Isolare](../test/isolating-code-under-test-with-microsoft-fakes.md)il codice sotto test con Microsoft Fakes .

**Requisiti**

- Visual Studio Enterprise
- Un progetto .NET Framework
::: moniker range=">=vs-2019"
- .NET Core, .NET 5.0 e i progetti di tipo SDK supportano l'anteprima in Visual Studio 2019 Update 6 ed è abilitato per impostazione predefinita nell'aggiornamento 8. Per altre informazioni, vedere [Microsoft Fakes per i progetti di tipo .NET Core e SDK.](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)
::: moniker-end

## <a name="example-the-y2k-bug"></a>Esempio: il bug dell'anno 2000

Si consideri un metodo che genera un'eccezione il 1° gennaio 2000:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Il test di questo metodo è problematico perché il programma dipende da `DateTime.Now`, un metodo che dipende dall'orologio del computer, ovvero un metodo che dipende dall'ambiente e non deterministico. `DateTime.Now` è anche una proprietà statica. Pertanto in questo caso non è possibile usare un tipo stub. Questo problema è sintomatico dell'isolamento nel testing unità: i programmi che eseguono chiamate direttamente nelle API di database, che comunicano con i servizi Web e così via sono difficili da sottoporre a unit test perché la loro logica dipende dall'ambiente.

In questi casi è necessario usare tipi shim. I tipi shim offrono un meccanismo di deviazione di qualsiasi metodo .NET a un delegato definito dall'utente. I tipi shim vengono generati dal codice dal generatore Fakes e usano delegati, detti tipi shim, per specificare le nuove implementazioni del metodo.

Il test seguente mostra come usare il tipo shim `ShimDateTime` per fornire un'implementazione personalizzata di DateTime.Now:

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()) {
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}
```

## <a name="how-to-use-shims"></a>Come utilizzare gli shim

Aggiungere prima di tutto un assembly Fakes seguente:

1. In **Esplora soluzioni**, 
    - Per un modello .NET Framework Project precedente (stile non SDK), espandere il unit test riferimenti **del** progetto.
    ::: moniker range=">=vs-2019"
    - Per un progetto di tipo SDK che ha come destinazione .NET Framework, .NET Core o .NET 5.0, espandere il nodo **Dipendenze** per trovare l'assembly da fingere in **Assembly**, **Progetti** o **Pacchetti**.
    ::: moniker-end
    - Se si sta lavorando in Visual Basic, selezionare **Mostra** tutti i file nella barra **degli strumenti** Esplora soluzioni per visualizzare il **nodo** Riferimenti.

2. Selezionare l'assembly che contiene le definizioni di classe per cui si desidera creare sms. Ad esempio, se si vuole eseguire lo shim **DateTime,** selezionare **System.dll**.

3. Scegliere **Aggiungi assembly Fakes** dal menu di scelta rapida.

### <a name="use-shimscontext"></a>Utilizzare ShimsContext

Quando si usano tipi shim in un framework unit test, eseguire il wrapping del codice di test in un oggetto per controllare la `ShimsContext` durata degli shim. In caso contrario, gli s shims durerebbero fino all'arresto di AppDomain. Il modo più semplice per creare un oggetto `ShimsContext` consiste nell'usare il metodo statico `Create()` come mostrato nel codice seguente:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

È fondamentale eliminare correttamente ogni contesto shim. Come regola generale, chiamare all'interno di un'istruzione per garantire la corretta `ShimsContext.Create` `using` cancellazione degli s shims registrati. Ad esempio, si potrebbe registrare uno shim per un metodo di test che sostituisce il metodo `DateTime.Now` con un delegato che restituisce sempre il primo gennaio 2000. Se si dimentica di cancellare lo shim registrato nel metodo di test, il resto dell'esecuzione dei test restituirà sempre il primo di gennaio 2000 come `DateTime.Now` valore . Ciò potrebbe sorprendere e confondere.

### <a name="write-a-test-with-shims"></a>Scrivere un test con shim

Nel codice di test inserire una *deviazione* per il metodo da simulare. Esempio:

```csharp
[TestClass]
public class TestClass1
{
        [TestMethod]
        public void TestCurrentYear()
        {
            int fixedYear = 2000;

            using (ShimsContext.Create())
            {
              // Arrange:
                // Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet =
                () =>
                { return new DateTime(fixedYear, 1, 1); };

                // Instantiate the component under test:
                var componentUnderTest = new MyComponent();

              // Act:
                int year = componentUnderTest.GetTheCurrentYear();

              // Assert:
                // This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year);
            }
        }
}
```

```vb
<TestClass()> _
Public Class TestClass1
    <TestMethod()> _
    Public Sub TestCurrentYear()
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
            Dim fixedYear As Integer = 2000
            ' Arrange:
            ' Detour DateTime.Now to return a fixed date:
            System.Fakes.ShimDateTime.NowGet = _
                Function() As DateTime
                    Return New DateTime(fixedYear, 1, 1)
                End Function

            ' Instantiate the component under test:
            Dim componentUnderTest = New MyComponent()
            ' Act:
            Dim year As Integer = componentUnderTest.GetTheCurrentYear
            ' Assert:
            ' This will always be true if the component is working:
            Assert.AreEqual(fixedYear, year)
        End Using
    End Sub
End Class
```

I nomi delle classi shim vengono creati aggiungendo un prefisso `Fakes.Shim` al nome del tipo originale.

Per usare gli shim è necessario inserire *deviazioni* nel codice dell'applicazione sottoposta a test. Laddove avviene una chiamata al metodo originale, il sistema Fake esegue una deviazione, in modo che anziché chiamare il metodo reale, chiama il codice dello shim.

Si noti che le deviazioni vengono create ed eliminate in fase di esecuzione. È necessario creare sempre una deviazione nella durata di un `ShimsContext`. Quando viene eliminato, qualsiasi shim creato mentre era attivo viene rimosso. Il modo migliore per eseguire questa operazione è all'interno di un'istruzione `using`.

Può verificarsi un errore di compilazione che informa che lo spazio dei nomi di Fake non esiste. L'errore talvolta viene visualizzato quando sono presenti altri errori di compilazione. Correggere gli altri errori e il problema viene risolto.

## <a name="shims-for-different-kinds-of-methods"></a>Shim per tipi di metodi differenti

I tipi shim consentono di sostituire qualsiasi metodo .NET, compresi i metodi statici o metodi non virtuali, con i delegati.

### <a name="static-methods"></a>Metodi statici

Le proprietà per associare gli shim ai metodi statici vengono inserite in un tipo shim. Ogni proprietà dispone solo di un setter che può essere usato per associare un delegato al metodo di destinazione. Si consideri ad esempio una classe `MyClass` con un metodo statico `MyMethod`:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

È possibile associare uno shim a `MyMethod` che restituisce sempre 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Metodi di istanza (per tutte le istanze)

Analogamente ai metodi statici, i metodi di istanza possono essere sottoposti a shim per tutte le istanze. Le proprietà a cui associare tali shim vengono inserite in un tipo annidato denominato AllInstances per evitare confusione. Si consideri, ad esempio, una classe `MyClass` con un metodo di istanza `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

È possibile associare uno shim a `MyMethod` che restituisce sempre 5, indipendentemente dall'istanza:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

La struttura del tipo generato di ShimMyClass è simile al codice seguente:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public static class AllInstances {
        public static Func<MyClass, int>MyMethod {
            set {
                ...
            }
        }
    }
}
```

Si noti che in questo caso Fakes passa l'istanza di runtime come primo argomento del delegato.

### <a name="instance-methods-for-one-runtime-instance"></a>Metodi di istanza (per un'istanza di runtime)

I metodi di istanza possono anche essere sottoposti a shim da delegati diversi, in base al destinatario della chiamata. In questo modo, lo stesso metodo di istanza può avere comportamenti diversi per ogni istanza del tipo. Le proprietà per impostare tali shim sono metodi di istanza del tipo shim stesso. Ogni tipo shim di cui viene creata un'istanza è anche associato a un'istanza non elaborata di un tipo sottoposto a shim.

Si consideri, ad esempio, una classe `MyClass` con un metodo di istanza `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

È possibile impostare due tipi shim di MyMethod in modo che il primo restituisca sempre 5 e il secondo restituisca sempre 10:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

La struttura del tipo generato di ShimMyClass è simile al codice seguente:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public Func<int> MyMethod {
        set {
            ...
        }
    }
    public MyClass Instance {
        get {
            ...
        }
    }
}
```

È possibile accedere all'istanza effettiva del tipo sottoposto a shim tramite la proprietà Instance:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Il tipo shim dispone anche di una conversione implicita nel tipo sottoposto a shim, pertanto in genere è sufficiente usare il tipo shim così com'è:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Costruttori

Anche i costruttori possono essere sottoposti a shim per associare tipi shim a oggetti futuri. Ogni costruttore viene esposto come costruttore di metodo statico nel tipo shim. Si consideri ad esempio una classe `MyClass` con un costruttore che accetta un valore intero:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Si imposta il tipo shim del costruttore in modo che tutte le istanze future restituiscano -5 quando viene richiamato il getter per il valore, indipendentemente dal valore nel costruttore:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Ogni tipo shim espone due costruttori. Il costruttore predefinito deve essere usato quando è necessaria una nuova istanza, mentre il costruttore che accetta un'istanza sottoposta a shim come argomento deve essere usato solo in shim del costruttore:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

La struttura del tipo generato di ShimMyClass è simile al codice seguente:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass>
{
    public static Action<MyClass, int> ConstructorInt32 {
        set {
            ...
        }
    }

    public ShimMyClass() { }
    public ShimMyClass(MyClass instance) : base(instance) { }
    ...
}
```

### <a name="base-members"></a>Membri di base

È possibile accedere alle proprietà degli shim dei membri di base creando uno shim per il tipo di base e passando l'istanza figlio come parametro al costruttore della classe shim di base.

Si consideri, ad esempio, una classe `MyBase` con un metodo di istanza `MyMethod` e un sottotipo `MyChild`:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

È possibile impostare uno shim di `MyBase` creando un nuovo shim `ShimMyBase`:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Si noti che il tipo shim figlio viene convertito in modo implicito nell'istanza figlio quando viene passato come parametro al costruttore shim di base.

La struttura dei tipi generati di ShimMyChild e ShimMyBase è simile al codice seguente:

```csharp
// Fakes generated code
public class ShimMyChild : ShimBase<MyChild> {
    public ShimMyChild() { }
    public ShimMyChild(Child child)
        : base(child) { }
}
public class ShimMyBase : ShimBase<MyBase> {
    public ShimMyBase(Base target) { }
    public Func<int> MyMethod
    { set { ... } }
}
```

### <a name="static-constructors"></a>Costruttori statici

I tipi shim espongono un metodo statico `StaticConstructor` per sottoporre a shim il costruttore statico di un tipo. Poiché i costruttori statici vengono eseguiti una sola volta, è necessario assicurarsi che lo shim sia configurato prima di accedere a qualsiasi membro del tipo.

### <a name="finalizers"></a>Finalizzatori

I finalizzatori non sono supportati in Fakes.

### <a name="private-methods"></a>Metodi privati

Il generatore di codice Fakes crea le proprietà dello shim per i metodi privati che hanno solo tipi visibili nella firma, ovvero i tipi di parametri e il tipo restituito visibile.

### <a name="binding-interfaces"></a>Interfacce di associazione

Quando un tipo sottoposto a shim implementa un'interfaccia, il generatore di codice genera un metodo che consente di associare contemporaneamente tutti i membri di tale interfaccia.

Si consideri, ad esempio, una classe `MyClass` che implementa `IEnumerable<int>`:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

È possibile eseguire lo shim delle implementazioni `IEnumerable<int>` di in MyClass chiamando il metodo Bind:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

La struttura del tipo generato di ShimMyClass è simile al codice seguente:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Modificare il comportamento predefinito

Ogni tipo shim generato include un'istanza dell'interfaccia `IShimBehavior`, tramite la proprietà `ShimBase<T>.InstanceBehavior`. Il comportamento viene usato ogni volta che un client chiama un membro di istanza che non è stato sottoposto a shim in modo esplicito.

Se il comportamento non è stato impostato in modo esplicito, viene usata l'istanza restituita dalla proprietà statica `ShimBehaviors.Current`. Per impostazione predefinita, questa proprietà restituisce un comportamento che genera un'eccezione `NotImplementedException`.

Il comportamento può essere modificato in qualsiasi momento impostando la proprietà `InstanceBehavior` su qualsiasi istanza di shim. Ad esempio, il frammento di codice seguente modifica lo shim in un comportamento che non esegue alcuna operazione o restituisce il valore predefinito del tipo restituito, ovvero `default(T)` :

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimBehaviors.DefaultValue;
```

Il comportamento può anche essere modificato a livello globale per tutte le istanze sottoposte a shim per le quali la proprietà `InstanceBehavior` non è stata impostata in modo esplicito impostando la proprietà statica `ShimBehaviors.Current`:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimBehaviors.Current = ShimBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Rilevare gli accessi nell'ambiente

È possibile associare un comportamento a tutti i membri, inclusi i metodi statici, di un determinato tipo assegnando il comportamento `ShimBehaviors.NotImplemented` alla proprietà statica `Behavior` del tipo shim corrispondente:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Concorrenza

I tipi shim si applicano a tutti i thread in AppDomain e non presentano affinità di thread. Questo è un fatto importante se si prevede di usare un test runner che supporta la concorrenza. I test che coinvolgono tipi shim non possono essere eseguiti contemporaneamente. Questa proprietà non viene applicata dal runtime di Fakes.

## <a name="call-the-original-method-from-the-shim-method"></a>Chiamare il metodo originale dal metodo shim

Imagine scrivere il testo nell'file system dopo la convalida del nome file passato al metodo . In tal caso, si chiamerà il metodo originale al centro del metodo shim.

Il primo approccio per risolvere questo problema consiste nell'eseguire il wrapping di una chiamata al metodo originale usando un delegato e `ShimsContext.ExecuteWithoutShims()` , come nel codice seguente:

```csharp
// unit test code
ShimFile.WriteAllTextStringString = (fileName, content) => {
  ShimsContext.ExecuteWithoutShims(() => {

      Console.WriteLine("enter");
      File.WriteAllText(fileName, content);
      Console.WriteLine("leave");
  });
};
```

Un altro approccio consiste nell'impostare lo shim su Null, chiamare il metodo originale e ripristinare lo shim.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter");
    // remove shim in order to call original method
    ShimFile.WriteAllTextStringString = null;
    File.WriteAllText(fileName, content);
  }
  finally
  {
    // restore shim
    ShimFile.WriteAllTextStringString = shim;
    Console.WriteLine("leave");
  }
};
// initialize the shim
ShimFile.WriteAllTextStringString = shim;
```

## <a name="systemenvironment"></a>System.Environment

Per shim <xref:System.Environment?displayProperty=fullName> aggiungere il contenuto seguente al file mscorlib.fakes dopo l'elemento **Assembly:**

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Dopo aver ricompilato la soluzione, i metodi e le proprietà nella classe sono disponibili per essere s <xref:System.Environment?displayProperty=fullName> shimmed, ad esempio:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Limitazioni

Gli s shims non possono essere usati in tutti i tipi della libreria di classi di base **.NET mscorlib** e **System** in .NET Framework e in **System.Runtime** in .NET Core o .NET 5.0.

## <a name="see-also"></a>Vedi anche

- [Isolare codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Blog di Peter Provost: Visual Studio 2012 sms](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): Test di codice non testabile con falsi in Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
