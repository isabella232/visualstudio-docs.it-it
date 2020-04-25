---
title: Introduzione agli unit test
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c167e98f9419842876aed713e008b8746064669a
ms.sourcegitcommit: dab57cebd484228e6f0cf7ab1b9685c575410c06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/25/2020
ms.locfileid: "82153044"
---
# <a name="get-started-with-unit-testing"></a>Introduzione agli unit test

Visual Studio consente di definire ed eseguire unit test per mantenere l'integrità del codice, garantire il code coverage e individuare gli errori e i problemi prima dei clienti. Eseguire gli unit test di frequente per assicurarsi che il codice funzioni correttamente.

## <a name="create-unit-tests"></a>Creare unit test

In questa sezione viene descritto come creare un progetto unit test.

1. Aprire il progetto da testare in Visual Studio.

   Per illustrare un esempio unit test, in questo articolo viene testato un semplice progetto "Hello World" denominato **HelloWorldCore**. Il codice di esempio per questo tipo di progetto è il seguente:

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. Selezionare il nodo della soluzione in **Esplora soluzioni**. Quindi, dalla barra dei menu superiore, selezionare **file** > **Aggiungi** > **nuovo progetto**.

1. Nella finestra di dialogo Nuovo progetto trovare e selezionare un modello di progetto di unit test per il framework di test che si vuole usare.

   ::: moniker range=">=vs-2019"

   ![Modello di progetto di unit test in Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Fare clic su **Avanti**, scegliere un nome per il progetto di test e quindi fare clic su **Crea**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Modello di progetto di unit test in Visual Studio 2019](media/mstest-test-project-template.png)

   Scegliere un nome per il progetto di test e quindi fare clic su **OK**.

   ::: moniker-end

   Il progetto viene aggiunto alla soluzione.

   ![Progetto di unit test in Esplora soluzioni](media/vs-2019/solution-explorer.png)

1. Nel progetto di unit test aggiungere un riferimento al progetto da testare facendo clic con il pulsante destro del mouse su **Riferimenti** o su **Dipendenze** e quindi scegliendo **Aggiungi riferimento**.

1. Selezionare il progetto che contiene il codice da testare e fare clic su **OK**.

   ![Aggiungere un riferimento al progetto in Visual Studio](media/vs-2019/reference-manager.png)

1. Aggiungere codice al metodo di unit test.

   Per un progetto MSTest, ad esempio, è possibile usare il codice seguente.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   In alternativa, per un progetto NUnit, è possibile usare il codice seguente.

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

> [!TIP]
> Per altri dettagli sulla creazione di unit test, vedere [creare ed eseguire unit test per codice gestito](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Eseguire unit test

1. Aprire [Esplora test](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Per aprire Esplora test, scegliere **test** > **Esplora** test dalla barra dei menu superiore.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Per aprire Esplora test, scegliere **test** > **Windows** > **Esplora test** di Windows dalla barra dei menu superiore.
   ::: moniker-end

1. Eseguire gli unit test facendo clic su **Esegui tutto**.

   ![Eseguire unit test in Esplora test](media/vs-2019/test-explorer-run-all.png)

   Dopo aver completato i test, un segno di spunta verde indica che un test è stato superato. Un'icona "x" rossa indica che un test non è stato superato.

   ![Esaminare i risultati degli unit test in Esplora test](media/vs-2019/unit-test-passed.png)

> [!TIP]
> È possibile usare [Esplora test](../test/run-unit-tests-with-test-explorer.md) per eseguire unit test dal framework di test integrato (MSTest) o da framework di test di terze parti. È possibile raggruppare i test in categorie, filtrare l'elenco dei test e creare, salvare ed eseguire playlist di test. È anche possibile eseguire il debug dei test e analizzare code coverage e prestazioni dei test.

## <a name="view-live-unit-test-results"></a>Visualizzare i risultati degli unit test in tempo reale

Se si usa il framework di test MSTest, xUnit o NUnit in Visual Studio 2017 o versione successiva, è possibile visualizzare in tempo reale i risultati degli unit test.

> [!NOTE]
> Live Unit Testing è disponibile solo nell'edizione Enterprise.

1. Attivare Live Unit Testing dal menu **Test**, scegliendo **Test** > **Live Unit Testing** > **Avvia**.

   ::: moniker range="vs-2017"

   ![Attivare Live Unit Testing](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Avviare Live Unit Testing in Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Visualizzare i risultati dei test nella finestra dell'editor di codice durante la scrittura e la modifica del codice.

   ![Visualizzare i risultati dei test](media/vs-2019/live-unit-testing-results.png)

1. Fare clic sull'indicatore del risultato di un test per visualizzare altre informazioni, ad esempio i nomi dei test che verificano tale metodo.

   ![Scegliere gli indicatori dei risultati dei test](media/vs-2019/live-unit-testing-details.png)

Per altre informazioni su Live Unit Testing, vedere [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generare unit test con IntelliTest

Quando si esegue IntelliTest, è possibile visualizzare i test non superati e aggiungere l'eventuale codice necessario per correggerli. È possibile scegliere quali dei test generati salvare in un progetto di test per fornire un gruppo di regressione. Quando si modifica il codice, eseguire nuovamente IntelliTest per mantenere i test generati sincronizzati con le modifiche apportate al codice. Per la procedura, vedere [Generare unit test per il codice con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest è disponibile solo per il codice gestito destinato a .NET Framework.

![Generare unit test con IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analizzare il code coverage

Per determinare quale percentuale del codice del progetto viene effettivamente testata dai test codificati come unit test, è possibile utilizzare la funzionalità code coverage di Visual Studio. Per una protezione efficace dai bug, i test devono mettere in pratica gran parte del codice. Per la procedura, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Usare un framework di test di terze parti

È possibile eseguire unit test in Visual Studio usando framework di test di terze parti come Boost, NUnit e Google. Usare **Gestione pacchetti NuGet** per installare il pacchetto NuGet per il framework di propria scelta. In alternativa, per i framework di test NUnit e xUnit, Visual Studio include modelli di progetto di test preconfigurati che includono i pacchetti NuGet necessari.

Per creare unit test che usano [NUnit](https://nunit.org/):

1. Aprire la soluzione che contiene il codice da testare.

2. Fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

3. Selezionare il modello di progetto **Progetto di test NUnit**.

   ::: moniker range=">=vs-2019"

   ![Modello di progetto di test NUnit in Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Fare clic su **Avanti**, assegnare un nome al progetto e quindi fare clic su **Crea**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Assegnare un nome al progetto e quindi fare clic su **OK** per crearlo.

   ::: moniker-end

   Il modello di progetto include i riferimenti NuGet di NUnit e NUnit3TestAdapter.

   ![Dipendenze NuGet di NUnit in Esplora soluzioni](media/vs-2019/nunit-nuget-dependencies.png)

4. Aggiungere un riferimento dal progetto di test al progetto che contiene il codice da testare.

   Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e quindi scegliere **Aggiungi** > **Riferimento**. È anche possibile aggiungere un riferimento dal menu di scelta rapida del nodo **Riferimenti** o **Dipendenze**.

5. Aggiungere codice al metodo di test.

   ![Aggiungere codice al file di codice dello unit test](media/vs-2019/unit-test-method.png)

6. Eseguire il test da **Esplora test** o facendo clic con il pulsante destro del mouse sul codice di test e scegliendo **Esegui test**.

## <a name="see-also"></a>Vedi anche

* [Procedura dettagliata: Creare ed eseguire unit test per codice gestito](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Comando Crea unit test](create-unit-tests-menu.md)
* [Generare unit test per il codice con IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md)
* [Analizzare il code coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
