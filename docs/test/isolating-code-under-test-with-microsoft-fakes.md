---
title: Isolamento del codice sottoposto a test con Microsoft Fakes
description: Informazioni su Microsoft Fakes consente di isolare il codice che si sta testando sostituendo altre parti dell'applicazione con stub o s shims.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 59ff08ed61704703bb547e2981860e1136ecbc7cc9d3abad04f77a19fd56a3a6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121227115"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Isolare codice sottoposto a test con Microsoft Fakes

Microsoft Fakes consente di isolare il codice di cui si sta eseguendo il test sostituendo altre parti dell'applicazione con *stub* o *shim*. Si tratta di frammenti di codice che rientrano nel controllo dei test. Isolando il codice per il test, si avrà la certezza che se il test non viene superato, la causa è presente in tale codice e non in un altro punto. Anche gli stub e gli shim consentono di testare il codice anche se altre parti dell'applicazione ancora non funzionano.

Fakes è di due tipi:

- Uno [stub](#get-started-with-stubs) sostituisce una classe con un componente di dimensioni ridotte che implementa la stessa interfaccia.  Per usare gli stub, è necessario progettare l'applicazione in modo che ogni componente dipenda solo dalle interfacce e non da altri componenti. Il termine "componente" indica una classe o un gruppo di classi progettate e aggiornate insieme che sono generalmente contenute in un assembly.

- Uno [shim](#get-started-with-shims) modifica il codice compilato dell'applicazione in fase di esecuzione in modo tale che, invece di effettuare la chiamata al metodo specificato, esegue il codice dello shim fornito dal test. Gli shim possono essere usati per sostituire le chiamate agli assembly che non si possono modificare, ad esempio gli assembly .NET.

![Fakes sostituisce altri componenti](../test/media/fakes-2.png)

**Requisiti**

- Visual Studio Enterprise
- Un progetto .NET Framework
::: moniker range=">=vs-2019"
- .NET Core, .NET 5.0 e il supporto di progetti in stile SDK sono stati visualizzati in anteprima in Visual Studio 2019 Update 6 ed è abilitato per impostazione predefinita nell'aggiornamento 8. Per altre informazioni, vedere [Microsoft Fakes per i progetti di tipo .NET Core e SDK.](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)
::: moniker-end

> [!NOTE]
> - La profilatura con Visual Studio non è disponibile per i test che usano Microsoft Fakes.

## <a name="choose-between-stub-and-shim-types"></a>Scegliere tra i tipi stub e shim
In genere, un progetto di Visual Studio viene considerato un componente perché le classi vengono sviluppate e aggiornate contemporaneamente. Considerare l'uso di stub e shim per le chiamate che il progetto effettua ad altri progetti della soluzione o ad altri assembly a cui fa riferimento.

In generale, è consigliabile usare gli stub per le chiamate all'interno della soluzione di Visual Studio e gli shim per le chiamate ad altri assembly a cui si fa riferimento. Questo perché all'interno di una soluzione è consigliabile separare i componenti definendo le interfacce secondo le regole di esecuzione dello stub. Tuttavia, gli assembly esterni come *System.dll* in genere non vengono forniti con definizioni di interfaccia separate, pertanto è necessario usare gli s shim.

Altre considerazioni:

**Prestazione.** Gli shim sono più lenti perché riscrivono il codice in fase di esecuzione. Gli stub non incorrono in questo sovraccarico delle prestazioni e sono veloci al pari dei metodi virtuali.

**Metodi statici, tipi sealed.** È possibile usare solo gli stub per implementare le interfacce. Di conseguenza, i tipi stub non possono essere usati per metodi statici, metodi non virtuali, metodi virtuali sealed, metodi con tipi sealed e così via.

**Tipi interni.** Sia i tipi stub che i tipi shim possono essere utilizzati con tipi interni che sono stati resi accessibili con l'attributo dell'assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.

**Metodi privati.** Gli shim possono sostituire le chiamate ai metodi privati se tutti i tipi sono visibili nella firma del metodo. Gli stub possono sostituire solo i metodi visibili.

**Interfacce e metodi astratti.** Gli stub forniscono implementazioni di interfacce e metodi astratti che possono essere utilizzati nel test. Gli shim non possono instrumentare interfacce e metodi astratti perché sono privi di corpi di metodo.

In generale, è consigliabile usare i tipi stub per l'isolamento dalle dipendenze nella codebase. A tale scopo è possibile nascondere i componenti dietro le interfacce. I tipi shim possono essere usati per l'isolamento da componenti di terze parti che non forniscono un'API testabile.

## <a name="get-started-with-stubs"></a>Introduzione agli stub
Per una descrizione più dettagliata, vedere [Usare stub per isolare le parti dell'applicazione l'una dall'altra per unit test](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Inserire le interfacce**

     Per usare gli stub, è necessario scrivere il codice che si desidera testare in modo che non menzioni esplicitamente le classi in un altro componente dell'applicazione. Il termine "componente" indica una o più classi sviluppate e aggiornate insieme che in genere sono contenute in un solo progetto di Visual Studio. Le variabili e i parametri devono essere dichiarati tramite le interfacce e le istanze di altri componenti devono essere passate o create tramite una factory. Ad esempio, se StockFeed è una classe in un altro componente dell'applicazione, allora questa viene considerata non valida:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Definire invece un'interfaccia che può essere implementata dall'altro componente e che può essere anche implementata da uno stub a scopo di test:

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Aggiungere l'assembly Fakes**

   1. In **Esplora soluzioni**, 
       - Per un progetto .NET Framework Project precedente (stile non SDK), espandere il unit test riferimenti **del** progetto.
       ::: moniker range=">=vs-2019"
       - Per un progetto di tipo SDK che ha come destinazione .NET Framework, .NET Core o .NET 5.0, espandere il nodo **Dipendenze** per trovare l'assembly che si vuole creare in **assembly,** progetti o **pacchetti.**
       ::: moniker-end
       - Se si sta lavorando in Visual Basic, selezionare **Mostra** tutti i file nella barra **degli strumenti Esplora soluzioni** per visualizzare il **nodo** Riferimenti.
   2. Selezionare l'assembly che contiene le definizioni di classe per cui si desidera creare s shims. Ad esempio, se si vuole eseguire lo shim **di DateTime**, **selezionareSystem.dll**.

   3. Scegliere **Aggiungi assembly Fakes** dal menu di scelta rapida.

3. Nei test, creare le istanze dello stub e fornire il codice per i relativi metodi:

    ```csharp
    [TestClass]
    class TestStockAnalyzer
    {
        [TestMethod]
        public void TestContosoStockPrice()
        {
          // Arrange:

            // Create the fake stockFeed:
            IStockFeed stockFeed =
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                     {
                         // Define each method:
                         // Name is original name + parameter types:
                         GetSharePriceString = (company) => { return 1234; }
                     };

            // In the completed application, stockFeed would be a real one:
            var componentUnderTest = new StockAnalyzer(stockFeed);

          // Act:
            int actualValue = componentUnderTest.GetContosoPrice();

          // Assert:
            Assert.AreEqual(1234, actualValue);
        }
        ...
    }
    ```

    ```vb
    <TestClass()> _
    Class TestStockAnalyzer

        <TestMethod()> _
        Public Sub TestContosoStockPrice()
            ' Arrange:
            ' Create the fake stockFeed:
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
            With stockFeed
                .GetSharePriceString = Function(company)
                                           Return 1234
                                       End Function
            End With
            ' In the completed application, stockFeed would be a real one:
            Dim componentUnderTest As New StockAnalyzer(stockFeed)
            ' Act:
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice
            ' Assert:
            Assert.AreEqual(1234, actualValue)
        End Sub
    End Class

    ```

    Il particolare speciale qui è la classe `StubIStockFeed`. Per ogni interfaccia nell'assembly di riferimento, il meccanismo Microsoft Fakes genera una classe stub. Il nome della classe stub deriva dal nome dell'interfaccia, con " " come prefisso e i nomi `Fakes.Stub` dei tipi di parametro aggiunti.

    Gli stub vengono generati per i metodi GET e SET di proprietà, per gli eventi e per i metodi generici. Per altre informazioni, vedere [Usare gli stub per isolare le parti dell'applicazione l'una dall'altra per gli unit test](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Introduzione agli shim
Per una descrizione più dettagliata, vedere [Usare shim per isolare l'applicazione da altri assembly per unit test](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

Si supponga che il componente contenga delle chiamate a `DateTime.Now`:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Durante un test, si desidera rendere shim la proprietà `Now` perché la versione reale utile restituisce in modo non conveniente un valore diverso a ogni chiamata.

Per usare gli shim, non è necessario modificare il codice dell'applicazione o scriverlo in un modo particolare.

1. **Aggiungere l'assembly Fakes**

     In **Esplora soluzioni** aprire i unit test del progetto e selezionare il riferimento all'assembly che contiene il metodo da fingere. In questo esempio la classe `DateTime` si trova in *System.dll*.  Per visualizzare i riferimenti in un progetto di Visual Basic, scegliere **Mostra tutti i file**.

     Scegliere **Aggiungi assembly Fakes**.

2. **Inserire uno shim in uno ShimsContext**

    ```csharp
    [TestClass]
    public class TestClass1
    {
            [TestMethod]
            public void TestCurrentYear()
            {
                int fixedYear = 2000;

                // Shims can be used only in a ShimsContext:
                using (ShimsContext.Create())
                {
                  // Arrange:
                    // Shim DateTime.Now to return a fixed date:
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

    I nomi delle classi shim vengono creati aggiungendo un prefisso `Fakes.Shim` al nome del tipo originale. I nomi dei parametri vengono aggiunti al nome del metodo. Non è necessario aggiungere riferimenti di assembly a System.Fakes.

Nell'esempio precedente viene usato uno shim come metodo statico. Per usare uno shim per un metodo di istanza, scrivere `AllInstances` tra il nome del tipo e il nome del metodo:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

Non c'è un assembly "System.IO.Fakes" a cui fare riferimento. Lo spazio dei nomi viene generato dal processo di creazione di shim. È tuttavia possibile usare istruzioni "using" o "import" nel modo consueto.

È inoltre possibile creare shim per istanze, costruttori e proprietà specifiche. Per altre informazioni, vedere [Usare shim per isolare l'applicazione da altri assembly per unit test](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="using-microsoft-fakes-in-the-ci"></a>Uso Microsoft Fakes nell'cia

### <a name="microsoft-fakes-assembly-generation"></a>Microsoft Fakes Generazione di assembly
Poiché Microsoft Fakes richiede Visual Studio Enterprise, per la generazione di Fakes assembly è necessario compilare il progetto usando l Visual Studio [di compilazione .](/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops&preserve-view=true)

::: moniker range=">=vs-2019"
> [!NOTE]
> Un'alternativa consiste nel archiviare Fakes assembly nell'cia e usare [l'attività MSBuild .](../msbuild/msbuild-task.md?view=vs-2019&preserve-view=true) In questo caso, è necessario assicurarsi di disporre di un riferimento all'assembly Fakes generato nel progetto di test, in modo simile al frammento di codice seguente:

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <ItemGroup>
        <Reference Include="FakesAssemblies\System.Fakes.dll"/>
    </ItemGroup>
</Project>
```

Questo riferimento deve essere aggiunto manualmente in progetti di tipo SDK (.NET Core, .NET 5.0 e .NET Framework) perché è stata aggiunta implicitamente riferimenti ad assembly al progetto di test. Se si segue questo metodo, è necessario assicurarsi che l'assembly fakes sia aggiornato quando l'assembly padre viene modificato.
::: moniker-end

### <a name="running-microsoft-fakes-tests"></a>Esecuzione di Microsoft Fakes test
Purché gli Microsoft Fakes siano presenti nella directory configurata (l'impostazione predefinita è ), è possibile eseguire i test `FakesAssemblies` `$(ProjectDir)FakesAssemblies` usando [l'attività vstest](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true).

::: moniker range=">=vs-2019"
Il test distribuito con l'attività [vstest](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true) .NET Core e i progetti .NET 5.0 che usano Microsoft Fakes richiede Visual Studio 2019 Update 9 Preview e `20201020-06` versioni successive.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="transitioning-your-net-framework-test-projects-that-use-microsoft-fakes-to-sdk-style-net-framework-net-core-or-net-50-projects"></a>Transizione dei progetti .NET Framework test che usano Microsoft Fakes a progetti di .NET Framework, .NET Core o .NET 5.0 di tipo SDK
Per eseguire la transizione a .NET Core o .NET 5.0, sono necessarie modifiche minime nel .NET Framework configurato per la Microsoft Fakes. I casi da considerare sono:
- Se si usa un modello di progetto personalizzato, è necessario assicurarsi che sia di tipo SDK e compilazioni per un framework di destinazione compatibile.
- Alcuni tipi esistono in assembly diversi in .NET Framework e .NET Core/.NET 5.0 (ad esempio in .NET Framework e in .NET Core e `System.DateTime` `System` / `mscorlib` .NET 5.0) e in questi scenari è necessario modificare `System.Runtime` l'assembly falsificato.
- Se si dispone di un riferimento all'assembly fakes e del progetto di test, è possibile che venga visualizzato un avviso di compilazione relativo a un riferimento mancante simile al seguente:
  ```
  (ResolveAssemblyReferences target) ->
  warning MSB3245: Could not resolve this reference. Could not locate the assembly "AssemblyName.Fakes". Check to make sure the assembly exists on disk.
  If this reference is required by your code, you may get compilation errors.
  ```
  Questo avviso è dovuto alle modifiche necessarie apportate nella generazione Fakes può essere ignorata. È possibile evitarlo rimuovendo il riferimento all'assembly dal file di progetto, perché ora vengono aggiunti in modo implicito durante la compilazione.
::: moniker-end

## <a name="microsoft-fakes-support"></a>Microsoft Fakes supporto 
### <a name="microsoft-fakes-in-older-projects-targeting-net-framework-non-sdk-style"></a>Microsoft Fakes nei progetti precedenti che hanno come destinazione .NET Framework (stile non SDK).
- Microsoft Fakes generazione di assembly è supportata in Visual Studio Enterprise 2015 e versioni successive.
- Microsoft Fakes test possono essere eseguiti con tutti i pacchetti NuGet Microsoft.TestPlatform disponibili.
- Il code coverage è supportato per i progetti di test Microsoft Fakes in Visual Studio Enterprise 2015 e versioni successive.

### <a name="microsoft-fakes-in-sdk-style-net-framework-net-core-and-net-50-projects"></a>Microsoft Fakes nei progetti di tipo SDK .NET Framework, .NET Core e .NET 5.0
- Microsoft Fakes generazione di assembly in anteprima Visual Studio Enterprise 2019 Update 6 ed è abilitata per impostazione predefinita nell'aggiornamento 8.
- Microsoft Fakes test per i progetti che hanno come destinazione .NET Framework possono essere eseguiti con tutti i pacchetti NuGet Microsoft.TestPlatform disponibili.
- Microsoft Fakes test per i progetti che hanno come destinazione .NET Core e .NET 5.0 possono essere eseguiti con pacchetti NuGet Microsoft.TestPlatform con versioni [16.9.0-preview-20210106-01](https://www.nuget.org/packages/Microsoft.TestPlatform/16.9.0-preview-20210106-01) e successive.
- Il code coverage è supportato per i progetti di test .NET Framework usando Microsoft Fakes in Visual Studio Enterprise versione 2015 e successive.
- Il supporto code coverage per i progetti di test per .NET Core e .NET 5.0 con Microsoft Fakes è disponibile nell'aggiornamento 9 Visual Studio 2019 e versioni successive.


## <a name="in-this-section"></a>Contenuto della sezione
[Usare stub per isolare le parti dell'applicazione l'una dall'altra per unit test](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Usare shim per isolare l'applicazione da altri assembly per unit test](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Generazione del codice, compilazione e convenzioni di denominazione in Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
