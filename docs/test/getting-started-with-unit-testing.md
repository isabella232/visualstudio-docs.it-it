---
title: Introduzione agli unit test
description: Usare Visual Studio definire ed eseguire unit test per mantenere l'integrità del codice e individuare errori ed errori prima che i clienti lo facciano.
ms.custom: SEO-VS-2020
ms.date: 08/10/2021
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 2465deef6d8b4c93b9e72d38bf548a001373f9e3
ms.sourcegitcommit: e6aeefef5b659a56e6e433d155bfd269c46bceb0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2021
ms.locfileid: "122603606"
---
# <a name="get-started-with-unit-testing"></a>Introduzione agli unit test

Visual Studio consente di definire ed eseguire unit test per mantenere l'integrità del codice, garantire il code coverage e individuare gli errori e i problemi prima dei clienti. Eseguire gli unit test di frequente per assicurarsi che il codice funzioni correttamente.

In questo articolo il codice usa C# e C++, le illustrazioni sono in C#, ma i concetti e le funzionalità si applicano ai linguaggi .NET, C++, Python, JavaScript e TypeScript.

## <a name="create-unit-tests"></a>Creare unit test

In questa sezione viene descritto come creare un unit test progetto.

1. Aprire il progetto da testare in Visual Studio.

   Ai fini della dimostrazione di un esempio unit test, questo articolo testa un semplice progetto console C# o C++ "Hello World" denominato **HelloWorld** (**HelloWorldCore** in C#). Il codice di esempio per questo tipo di progetto è il seguente:

   ### <a name="net"></a>[.NET](#tab/dotnet)
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

   ### <a name="c"></a>[C++](#tab/cpp)
   ```cpp
   #include <iostream>

   int main()
   {
      std::cout << "Hello World!\n";
   }
   ```
   ---

1. Selezionare il nodo della soluzione in **Esplora soluzioni**. Nella barra dei menu superiore selezionare **Quindi** Aggiungi nuovo file Project  >    >  .

1. Nella finestra di dialogo Nuovo progetto individuare il unit test da usare.

   ::: moniker range=">=vs-2019"
   Digitare **test** nella casella di ricerca per trovare un modello di progetto unit test per il framework di test che si vuole usare, ad esempio MSTest (C#) o il progetto **di unit test** nativo (C++) e selezionarlo.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Espandere il **nodo** Installato, scegliere il linguaggio che si vuole usare per il progetto di test e quindi scegliere **Test**.
   ::: moniker-end

   A partire Visual Studio 2017 versione 14.8, i linguaggi .NET includono modelli predefiniti per NUnit e xUnit. Per C++, in questo esempio selezionare il **progetto di unit test** nativo, che usa il framework di unit test nativo Microsoft. Per usare un framework di test C++ diverso, vedere [Scrittura di unit test per C/C++.](../test/writing-unit-tests-for-c-cpp.md) Per Python, vedere [Configurare unit test nel codice Python per](../python/unit-testing-python-in-visual-studio.md) configurare il progetto di test.

   > [!TIP]
   > Solo per C#, è possibile creare progetti unit test dal codice usando un metodo più veloce. Per altre informazioni, vedere [Creare progetti unit test e metodi di test.](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods-c) Per usare questo metodo con .NET Core o .NET Standard, è Visual Studio 2019.

   La figura seguente mostra un unit test MSTest, supportato in .NET.

   ::: moniker range=">=vs-2019"

   ![Modello di progetto di unit test in Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Fare clic su **Avanti**, scegliere un nome per il progetto di test e quindi fare clic su **Crea**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Modello di progetto di unit test in Visual Studio 2019](media/mstest-test-project-template.png)

   Scegliere un nome per il progetto di test, ad esempio HelloWorldTests, quindi fare clic su **OK.**

   ::: moniker-end

   Il progetto viene aggiunto alla soluzione.

   ![Progetto di unit test in Esplora soluzioni](media/vs-2019/solution-explorer.png)

1. Nel progetto unit test aggiungere un riferimento al progetto che si vuole testare  facendo clic con  il pulsante destro del mouse su Riferimenti o dipendenze e quindi scegliendo Aggiungi riferimento o Aggiungi riferimento **Project progetto.** 

1. Selezionare il progetto che contiene il codice da testare e fare clic su **OK**.

   ![Aggiungere un riferimento al progetto in Visual Studio](media/vs-2019/reference-manager.png)

1. Aggiungere codice al metodo di unit test.

   Ad esempio, è possibile usare il codice seguente selezionando la scheda della documentazione corretta corrispondente al framework di test: MSTest, NUnit o xUnit (supportato solo in .NET) o C++ Microsoft Native Unit Test Framework.

   ### <a name="mstest"></a>[MSTest](#tab/mstest)

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

   ### <a name="nunit"></a>[NUnit](#tab/nunit)

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

    ### <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

    ### <a name="microsoft-native-unit-test-framework"></a>[Framework di unit test nativo Microsoft](#tab/msunittest)

    ```cpp
    #include "pch.h"
    #include "CppUnitTest.h"
    #include "../HelloWorldUnitTestCPP/HelloWorldUnitTestCPP.cpp"   // Update using your project name

    using namespace Microsoft::VisualStudio::CppUnitTestFramework;

    namespace HelloWorldTests
    {
       TEST_CLASS(HelloWorldTests)
       {
       public:

          TEST_METHOD(TestMethod)
          {
             std::string expected = "Hello World!\n";

             std::stringstream buffer;
             std::streambuf* sbuf = std::cout.rdbuf(); // Save cout's buffer
             std::cout.rdbuf(buffer.rdbuf()); // Redirect cout to the stringstream buffer

             // Call main() in your test
             int result = main();

             // When finished, redirect cout to the original buffer 
             std::cout.rdbuf(sbuf);
             std::cout << "std original buffer: \n";
             std::cout << buffer.get();

             // Test
             Assert::AreEqual(expected, buffer.str());
          }
       };
    }
    ```

    ---

## <a name="run-unit-tests"></a>Eseguire unit test

1. Aprire [Esplora test](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Per aprire Esplora test, scegliere **Esplora** > **test dalla** barra dei menu superiore oppure premere **CTRL** + **E**, **T**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Per aprire Esplora  test, scegliere > **Test Windows** Esplora > **test** dalla barra dei menu superiore.
   ::: moniker-end

1. Eseguire gli unit test facendo clic **su Esegui tutto** (o premere **CTRL**  +  **R**, **V**).

   ![Eseguire unit test in Esplora test](media/vs-2019/test-explorer-run-all.png)

   Dopo aver completato i test, un segno di spunta verde indica che un test è stato superato. Un'icona "x" rossa indica che un test non è stato superato.

   ![Esaminare i risultati degli unit test in Esplora test](media/vs-2019/unit-test-passed.png)

> [!TIP]
> È possibile usare [Esplora test](../test/run-unit-tests-with-test-explorer.md) per eseguire unit test dal framework di test integrato (MSTest) o da framework di test di terze parti. È possibile raggruppare i test in categorie, filtrare l'elenco dei test e creare, salvare ed eseguire playlist di test. È anche possibile eseguire il debug dei test e analizzare code coverage e prestazioni dei test.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Visualizzare i risultati unit test live (Visual Studio Enterprise)

Se si usa il framework di test MSTest, xUnit o NUnit in Visual Studio 2017 o versione successiva, è possibile visualizzare in tempo reale i risultati degli unit test.

> [!NOTE]
> Per seguire questa procedura, Visual Studio Enterprise necessario, insieme al codice .NET e a uno dei framework di test seguenti: MSTest, xUnit o NUnit.

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

## <a name="use-a-third-party-test-framework"></a>Usare un framework di test di terze parti

È possibile eseguire unit test in Visual Studio usando framework di test di terze parti, ad esempio NUnit, Boost o Google C++ Testing Framework, a seconda del linguaggio di programmazione. Per usare un framework di terze parti:

- Usare **Gestione pacchetti NuGet** per installare il pacchetto NuGet per il framework di propria scelta.

- (.NET) A partire Visual Studio 2017 versione 14.6, Visual Studio include modelli di progetto di test preconfigurato per i framework di test NUnit e xUnit. I modelli includono anche i pacchetti di NuGet necessari per abilitare il supporto.

- (C++) In Visual Studio 2017 e versioni successive sono già inclusi alcuni framework come Google C++ Testing Framework. Per altre informazioni, vedere [Scrivere unit test per C/C++ in Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

Per aggiungere un unit test progetto:

1. Aprire la soluzione che contiene il codice da testare.

2. Fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

3. Selezionare un modello unit test progetto di distribuzione.

   In questo esempio selezionare [NUnit](https://nunit.org/)

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

6. Eseguire il test da **Esplora test o** facendo clic con il pulsante destro del mouse sul codice di test e scegliendo Esegui test (o **CTRL**   +  **R**, **T**).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Nozioni di base sugli unit test](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Creare ed eseguire unit test per codice gestito](walkthrough-creating-and-running-unit-tests-for-managed-code.md)

> [!div class="nextstepaction"]
> [Scrivere unit test per C/C++](../test/writing-unit-tests-for-c-cpp.md)
