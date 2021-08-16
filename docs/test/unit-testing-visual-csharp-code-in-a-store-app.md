---
title: Testing unità di codice Visual C#
description: Informazioni su come creare unit test per una classe C# in un'app UWP. Questo articolo illustra lo sviluppo basato su test.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
ms.openlocfilehash: 73120c008e8a98500e721099b14a648aadf7eefed0afd9f487e72d06129ae1c8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384770"
---
# <a name="unit-test-c-code"></a>Unit test di codice C#

Questo articolo descrive un metodo per la creazione di unit test per una classe C# in un'app per la piattaforma UWP.

La **classe Rooter,** ovvero la classe testata, implementa una funzione che calcola una stima della radice quadrata di un determinato numero.

Questo articolo illustra *lo sviluppo basato su test.* In questo approccio si scrive prima un test che verifica un comportamento specifico nel sistema che si sta testando e quindi si scrive il codice che supera il test.

## <a name="create-the-solution-and-the-unit-test-project"></a>Creare la soluzione e il progetto unit test

1. Nel menu **File**, scegliere **Nuovo** > **Progetto**.

2. Cercare e selezionare il modello di progetto **App vuota (Windows universale)**.

3. Assegnare al progetto il **nome Maths**.

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Aggiungi**  >  **nuovo Project**.

5. Cercare e selezionare il modello di progetto **App unit test (Windows universale)**.

6. Assegnare al progetto di test **il nome RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Verificare che i test siano eseguiti in Esplora test

1. Inserire codice di test in **TestMethod1** nel file *UnitTest.cs:*

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   La <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe fornisce diversi metodi statici che è possibile usare per verificare i risultati nei metodi di test.

::: moniker range="vs-2017"

2. Scegliere **Esegui** tutti i test **dal** menu > **Test**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Scegliere **Esegui** tutti i test dal menu **Test**.

::: moniker-end

   Il progetto di test viene compilato ed eseguito. Sii paziente perché potrebbe essere necessario un po' di tempo. Viene **visualizzata la finestra** Esplora test e il test è elencato in Test **superati**. Il **riquadro** Riepilogo nella parte inferiore della finestra fornisce dettagli aggiuntivi sul test selezionato.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Aggiungere la classe Rooter al progetto Maths

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto Maths** e quindi scegliere **Aggiungi**  >  **classe**.

2. Assegnare il nome *Rooter.cs* al file di classe.

3. Aggiungere il codice seguente al file *Rooter.cs della classe* **Rooter:**

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

   La **classe Rooter** dichiara un costruttore e il metodo dello estimatore **SquareRoot.** Il **metodo SquareRoot** è solo un'implementazione minima, sufficiente per testare la struttura di base della configurazione di test.

4. Aggiungere la `public` parola chiave alla dichiarazione della classe **Rooter,** in modo che il codice di test possa accedervi.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Aggiungere un riferimento al progetto

1. Aggiungere un riferimento dal progetto RooterTests all'app Maths.

    1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto RooterTests** e quindi scegliere **Aggiungi**  >  **riferimento**.

    2. Nella finestra di dialogo **Aggiungi riferimento - RooterTests** espandere **Soluzione** e scegliere **Progetti**. Selezionare il **progetto Maths.**

        ![Aggiungere un riferimento al progetto Maths](../test/media/ute_cs_windows_addreference.png)

2. Aggiungere `using` un'istruzione al file *UnitTest.cs:*

    1. Aprire *UnitTest.cs.*

    2. Aggiungi questo codice sotto la riga `using Microsoft.VisualStudio.TestTools.UnitTesting;`:

       ```csharp
       using Maths;
       ```

3. Aggiungere un test che usa la **funzione Rooter.** Aggiungere il codice seguente a *UnitTest.cs*:

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

4. Per evitare un errore "Payload contains two or more files with the same  destination path" (Payload contiene due o più file con lo stesso percorso di destinazione), in **Esplora soluzioni** espandere il nodo Proprietà nel progetto **Maths** e quindi eliminare il file *Default.rd.xml.*

::: moniker range="vs-2017"

6. In **Esplora test** scegliere Esegui **tutto**.

   Le compilazioni della soluzione e i test vengono eseguiti e superati.

   ![BasicTest passato in Esplora test](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. In **Esplora test** scegliere Esegui tutti i **test**.

   Le compilazioni della soluzione e i test vengono eseguiti e superati.

   ![Test di base superato in Esplora test](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Sono stati impostati i progetti di test e app e si è verificato che sia possibile eseguire test che chiamano funzioni nel progetto dell'app. Ora è possibile iniziare a scrivere test e codici reali.

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

2. Eseguire il test **RangeTest** e verificare che non riesca.

   ![RangeTest non riuscito](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Subito dopo aver scritto un test, eseguirlo per verificare che non riesca. Questo consente di evitare il semplice errore di scrivere un test che riesce sempre.

3. Modifica il codice sottoposto a test in modo che il nuovo test venga superato. Modificare la **funzione SquareRoot** in *Rooter.cs* in questo modo:

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

4. In **Esplora test** scegliere Esegui **tutto**.

::: moniker-end

::: moniker range=">=vs-2019"

4. In **Esplora test** scegliere Esegui tutti i **test**.

::: moniker-end

   Ora tutti e tre i test vengono superati.

> [!TIP]
> Sviluppare il codice aggiungendo un test alla volta. Assicurarsi che tutti i test vengano superati dopo ogni iterazione.

## <a name="refactor-the-code"></a>Eseguire il refactoring del codice

In questa sezione si effettua il refactoring sia del codice dell'app che del codice di test, quindi si rieseguino i test per assicurarsi che siano ancora superati.

### <a name="simplify-the-square-root-estimation"></a>Semplificare la stima della radice quadrata

1. Semplificare il calcolo centrale nella **funzione SquareRoot** modificando una riga di codice, come indicato di seguito:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Eseguire tutti i test per assicurarsi di non aver introdotto una regressione. Devono essere tutti passati.

> [!TIP]
> Un set stabile di unit test corretti indica con sufficiente sicurezza che non sono stati introdotti bug in fase di modifica del codice.

### <a name="eliminate-duplicated-code"></a>Eliminare il codice duplicato

Il **metodo RangeTest** imposta come hard code il denominatore della variabile *di* tolleranza passata al <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodo . Se si prevede di aggiungere altri test che usano lo stesso calcolo della tolleranza, l'uso di un valore hard-coded in più posizioni rende il codice più difficile da gestire.

1. Aggiungere un metodo helper privato alla **classe UnitTest1** per calcolare il valore di tolleranza e quindi chiamare tale metodo **da RangeTest**.

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
> Se si aggiunge un metodo helper a una classe di test e non si vuole che venga visualizzato in **Esplora** test, non aggiungere l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> al metodo.

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Sviluppo basato su test con Esplora test](quick-start-test-driven-development-with-test-explorer.md)
