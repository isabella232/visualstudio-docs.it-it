---
title: Procedura dettagliata sullo sviluppo basato su test
description: Informazioni su come sviluppare un metodo testato in C# usando Microsoft Test Framework, che è possibile adattare facilmente ad altri linguaggi o framework di test, ad esempio NUnit.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: de154900bee2c78453f559c8c90020147e8c528c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106653"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Procedura dettagliata: Sviluppo basato su test con Esplora test

Creare unit test per garantire il corretto funzionamento del codice attraverso modifiche incrementali. Esistono diversi framework che possono essere utilizzati per scrivere unit test, tra i quali alcuni sviluppati da terze parti. Alcuni framework di test sono specializzati per il testing in diversi linguaggi o piattaforme. Esplora test fornisce una singola interfaccia per gli unit test per uno qualsiasi di questi framework. Per altre informazioni su **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md) e [Domande frequenti su Esplora test](test-explorer-faq.md).

Questa procedura dettagliata illustra come sviluppare un metodo testato in C# usando il framework di test Microsoft (MSTest). È possibile adattare facilmente la procedura per altri linguaggi o altri framework di test, ad esempio NUnit. Per altre informazioni, vedere [Installare framework di unit test di terze parti.](install-third-party-unit-test-frameworks.md)

## <a name="create-a-test-and-generate-code"></a>Creare un test e generare codice

1. Creare un progetto **Libreria di classi (.NET Standard)** C#. Questo progetto conterrà il codice da testare. Assegnare al progetto il nome **MyMath**.

2. Nella stessa soluzione aggiungere un nuovo progetto di test MSTest.

   A partire da Visual Studio 2019 versione 16.9, il nome del modello di progetto MSTest è stato modificato da **MSTest Test Project (.NET Core)** a **Unit Test Project**.

   Assegnare al progetto di test il nome **MathTests**.

   ![Nuovo codice e progetti di test](../test/media/test-driven-development-ide.png)

3. Scrivere un metodo di test semplice che verifica il risultato ottenuto per un input specifico. Aggiungere il codice seguente alla classe `UnitTest1`:

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Generare un tipo dal codice di test.

   1. Posizionare il cursore su , quindi scegliere Genera tipo `Rooter` **'Rooter'** Genera nuovo tipo dal menu  >  **lampadina.**

      ![Azione rapida Genera nuovo tipo](media/test-driven-development-generate-new-type.png)

   2. Nella finestra di dialogo **Genera tipo** impostare **Progetto** su **MyMath**, il progetto libreria di classi, e quindi scegliere **OK**.

      ![Finestra di dialogo Genera tipo in Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Generare un metodo dal codice di test. Posizionare il cursore su `SquareRoot` e quindi dal menu Lampadina scegliere **Genera il metodo 'Rooter.SquareRoot'**.

6. Eseguire lo unit test.

   1. Per aprire **Esplora test**, dal menu **Test** scegliere **Finestre** > **Esplora test**.

   2. In **Esplora test** fare clic sul pulsante **Esegui tutto** per eseguire il test.

   La soluzione verrà compilata e il test verrà eseguito e avrà esito negativo.

7. Selezionare il nome del test.

   I dettagli del test vengono visualizzati nel riquadro **Riepilogo dettagli test**.

   ![Riepilogo dettagli test in Esplora test](media/test-driven-development-test-detail-summary.png)

8. Selezionare il collegamento superiore in **Analisi dello stack** per passare alla posizione in cui si è verificato l'errore nel test.

A questo punto sono stati creati un test e uno stub che è possibile modificare in modo che il test abbia esito positivo.

## <a name="verify-a-code-change"></a>Verificare una modifica del codice

1. Nel file *Class1.cs* migliorare il codice di `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. In **Esplora test** scegliere Esegui **tutto.**

   La soluzione verrà compilata e il test verrà eseguito e avrà esito positivo.

   ![Esplora test con test superato](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Estendere l'intervallo degli input

Per migliorare le probabilità che il codice funzioni in tutti i casi, aggiungere test che usano una gamma più ampia di valori di input.

> [!TIP]
> Evitare di modificare i test esistenti che hanno avuto successo. Piuttosto, aggiungere nuovi test. Modificare i test esistenti solo in caso di variazione dei requisiti dell'utente. Questo criterio assicura che le funzionalità esistenti non vadano perse mentre si lavora per estendere il codice.

1. Nella classe di test aggiungere il test seguente, che usa un intervallo di valori di input:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. In **Esplora test** scegliere Esegui **tutto.**

   Il nuovo test ha esito negativo nonostante il primo test abbia comunque esito positivo. Per trovare il punto di errore, selezionare il test con esito negativo e quindi esaminare i dettagli nel riquadro **Riepilogo dettagli test**.

3. Controllare il metodo sottoposto al test per vedere quale potrebbe essere l'errore. Modificare il codice di `SquareRoot` come illustrato di seguito:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. In **Esplora test** scegliere Esegui **tutto.**

   Ora entrambi i test avranno esito positivo.

## <a name="add-tests-for-exceptional-cases"></a>Aggiungere test per i casi eccezionali

1. Aggiungere un nuovo test per gli input negativi:

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. In **Esplora test** scegliere Esegui **tutto.**

   Il metodo sottoposto al test entra in un ciclo e deve essere annullato manualmente.

3. Scegliere **Annulla** sulla barra degli strumenti di **Esplora test**.

   L'esecuzione del test viene interrotta.

4. Correggere il codice di `SquareRoot` aggiungendo l'istruzione `if` seguente all'inizio del metodo:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. In **Esplora test** scegliere Esegui **tutto.**

   Tutti i test avranno esito positivo.

## <a name="refactor-the-code-under-test"></a>Effettuare il refactoring del codice sottoposto a test

Effettuare il refactoring del codice, ma non modificare i test.

> [!TIP]
> Un *refactoring* è una modifica finalizzata a migliorare le prestazioni del codice o a rendere il codice più facile da comprendere. Non è concepito per modificare il comportamento del codice e pertanto i test non vengono modificati.
>
> Si consiglia di effettuare le operazioni di refactoring separatamente dai passaggi che estendono le funzionalità. Mantenendo i test invariati ci si assicura che non siano stati introdotti accidentalmente bug durante il refactoring.

1. Modificare la riga che calcola `result` nel metodo `SquareRoot` come indicato di seguito:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. Scegliere **Esegui tutto** e verificare che tutti i test abbiano ancora esito positivo.

   ![Esplora test con 3 test superati](../test/media/test-driven-development-three-passed-tests.png)
