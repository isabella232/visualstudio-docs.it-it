---
title: Testing unità di codice Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590865"
---
# <a name="unit-test-c-code"></a>Unit test di codice C#

Questo articolo descrive un metodo per la creazione di unit test per una classe C# in un'app per la piattaforma UWP.

La classe **Rooter,** che è la classe sottoposta a test, implementa una funzione che calcola una stima della radice quadrata di un determinato numero.

In questo articolo viene illustrato *lo sviluppo basato su test.* In questo approccio, si scrive innanzitutto un test che verifica un comportamento specifico nel sistema che si sta testando e quindi si scrive il codice che supera il test.

## <a name="create-the-solution-and-the-unit-test-project"></a>Creare la soluzione e il progetto unit test

1. Nel menu **File**, scegliere **Nuovo** > **Progetto**.

2. Cercare e selezionare il modello di progetto **App vuota (Windows universale)**.

3. Assegnare al progetto il nome **Maths**.

4. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione e **scegliere Aggiungi** > **nuovo progetto**.

5. Cercare e selezionare il modello di progetto **App unit test (Windows universale)**.

6. Assegnare al progetto di test il nome **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Verificare che i test siano eseguiti in Esplora test

1. Inserire del codice di test in **TestMethod1** nel file *UnitTest.cs:*

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   La <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe fornisce diversi metodi statici che è possibile utilizzare per verificare i risultati nei metodi di test.

::: moniker range="vs-2017"

2. Nel menu **Test** scegliere **Esegui** > **Tutti i test**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Scegliere Esegui tutti **i test**dal menu **Test** .

::: moniker-end

   Il progetto di test viene compilato ed eseguito. Sii paziente perché potrebbe volerci un po'. Verrà **visualizzata** la finestra Esplora test e il test è elencato in **Test superati**. Il riquadro **Riepilogo** nella parte inferiore della finestra fornisce ulteriori dettagli sul test selezionato.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Aggiungere la classe Rooter al progetto Maths

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **Maths,** quindi **scegliere Aggiungi** > **classe**.

2. Assegnare il nome *Rooter.cs* al file di classe.

3. Aggiungere il codice seguente al file *di Rooter.cs* di classe **Rooter:**

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   La classe **Rooter** dichiara un costruttore e il metodo di stima **SquareRoot.** Il metodo **SquareRoot** è solo un'implementazione minima, quanto basta per testare la struttura di base dell'impostazione di test.

4. Aggiungere `public` la parola chiave alla dichiarazione della classe **Rooter,** in modo che il codice di test possa accedervi.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Aggiungere un riferimento al progetto

1. Aggiungere un riferimento dal progetto RooterTests all'app Maths.Add a reference from the RooterTests project to the Maths app.

    1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **RooterTests,** quindi **scegliere Aggiungi** > **riferimento**.

    2. Nella finestra di dialogo **Aggiungi riferimento - RooterTests** espandere **Soluzione** e scegliere **Progetti**. Selezionare il progetto **Matematica.**

        ![Aggiungere un riferimento al progetto Maths](../test/media/ute_cs_windows_addreference.png)

2. Aggiungere `using` un'istruzione al file *UnitTest.cs:*

    1. Aprire *UnitTest.cs*.

    2. Aggiungi questo codice sotto la riga `using Microsoft.VisualStudio.TestTools.UnitTesting;`:

       ```csharp
       using Maths;
       ```

3. Aggiungere un test che utilizza la funzione **Rooter.Add a test** that uses the Rooter function. Aggiungere il codice seguente a *UnitTest.cs*:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

   Il nuovo test viene visualizzato in **Esplora test** nel nodo Test **non eseguiti.**

4. Per evitare un errore "Payload contiene due o più file con lo stesso percorso di destinazione", in **Esplora soluzioni**espandere il nodo **Proprietà** nel progetto **Maths,** quindi eliminare il file *Default.rd.xml.*

::: moniker range="vs-2017"

6. In **Esplora test**scegliere Esegui **tutto**.

   La soluzione viene compilata e i test vengono eseguiti e superati.

   ![BasicTest passed in Test Explorer](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. In **Esplora test**scegliere Esegui tutti i **test**.

   La soluzione viene compilata e i test vengono eseguiti e superati.

   ![Test di base superato in Esplora testBasic Test passed in Test Explorer](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Hai configurato i progetti di test e app e hai verificato che puoi eseguire test che chiamano funzioni nel progetto dell'app. Ora è possibile iniziare a scrivere test e codici reali.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Aumentare i test in maniera iterativa e farli superare

1. Aggiungere un nuovo test denominato **RangeTest**:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > È consigliabile non modificare i test che siano stati superati. Aggiungere invece un nuovo test.

2. Eseguire il test **RangeTest** e verificare che abbia esito negativo.

   ![RangeTest non riuscito](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Immediatamente dopo aver scritto un test, eseguirlo per verificare che abbia esito negativo. Questo consente di evitare il semplice errore di scrivere un test che riesce sempre.

3. Modifica il codice sottoposto a test in modo che il nuovo test venga superato. Modificare la funzione **SquareRoot** in *Rooter.cs* in questo modo:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

::: moniker range="vs-2017"

4. In **Esplora test**scegliere Esegui **tutto**.

::: moniker-end

::: moniker range=">=vs-2019"

4. In **Esplora test**scegliere Esegui tutti i **test**.

::: moniker-end

   Ora tutti e tre i test vengono superati.

> [!TIP]
> Sviluppare il codice aggiungendo un test alla volta. Assicurarsi che tutti i test vengano superati dopo ogni iterazione.

## <a name="refactor-the-code"></a>Eseguire il refactoring del codice

In questa sezione si esegue il refactoring dell'app e del codice di test, quindi si eseguono nuovamente i test per assicurarsi che vengano comunque superati.

### <a name="simplify-the-square-root-estimation"></a>Semplificare la stima della radice quadrata

1. Semplificare il calcolo centrale nella funzione **SquareRoot** modificando una riga di codice, come segue:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Eseguire tutti i test per assicurarsi di non aver introdotto una regressione. Dovrebbero passare tutti.

> [!TIP]
> Un set stabile di unit test corretti indica con sufficiente sicurezza che non sono stati introdotti bug in fase di modifica del codice.

### <a name="eliminate-duplicated-code"></a>Eliminare il codice duplicato

Il metodo **RangeTest** codifica a disco il denominatore della <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> variabile di *tolleranza* passata al metodo. Se si prevede di aggiungere ulteriori test che utilizzano lo stesso calcolo della tolleranza, l'utilizzo di un valore hardcoded in più ubicazioni rende il codice più difficile da gestire.

1. Aggiungere un metodo helper privato alla classe **UnitTest1** per calcolare il valore di tolleranza, quindi chiamare tale metodo da **RangeTest**.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. Eseguire **RangeTest** per assicurarsi che passi ancora.

> [!TIP]
> Se si aggiunge un metodo di supporto a una classe di test e non si <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> desidera che venga visualizzato in Esplora **test**, non aggiungere l'attributo al metodo.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: sviluppo basato su test tramite Esplora testWalkthrough: Test-driven development using Test Explorer](quick-start-test-driven-development-with-test-explorer.md)
