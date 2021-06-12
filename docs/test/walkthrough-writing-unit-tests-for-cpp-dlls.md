---
title: 'Procedura: Scrivere unit test per DLL C/C++'
description: Informazioni su come sviluppare una DLL C++ nativa usando la metodologia test-first. Iniziare creando un progetto di test nativo.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: cfdc580b94760cb0c5160918210ba6c3dd8fa2f6
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042925"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Procedura: Scrivere unit test per DLL C/C++

Questa procedura dettagliata descrive come sviluppare una DLL C++ nativa usando la metodologia dei test preventivi. I passaggi di base sono i seguenti:

1. [Creare un progetto di test nativo](#create_test_project). Il progetto di test si trova nella stessa soluzione del progetto DLL.

2. [Creare un progetto DLL](#create_dll_project). In questa procedura dettagliata viene creato un nuovo file DLL, ma la procedura per testare una DLL esistente è simile.

3. [Definire le funzioni DLL visibili ai test](#make_functions_visible).

4. [Aumentare i test iterativamente](#iterate). Si consiglia un ciclo "red-green-refactor", in cui lo sviluppo di codice è condotto dai test.

5. [Debug di test non superati](#debug). È possibile eseguire test in modalità debug.

6. [Effettuare il refactoring mantenendo i test invariati](#refactor). Il refactoring indica il miglioramento della struttura del codice senza modificarne il comportamento esterno. È possibile eseguirla per migliorare prestazioni, estendibilità o leggibilità del codice. Poiché lo scopo non è di modificare il comportamento, non si modificano i test mentre si esegue il refactoring del codice. I test consentono di verificare che non vengano inseriti bug durante il refactoring.

7. [Controllo del code coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md). I test d'unità sono particolarmente utili quando eseguono più parti del codice. È possibile individuare quali parti del codice sono state usate dai test.

8. [Unità isolate da risorse esterne](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). In genere, una DLL dipende da altri componenti del sistema che si sta sviluppando, come altre DLL, i database, o dei sottosistemi remoti. È utile verificare ogni unità in isolamento dalle relative dipendenze. I componenti esterni possono provocare un rallentamento dell'esecuzione dei test. Durante lo sviluppo, gli altri componenti potrebbero non essere completati.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a> Creare un progetto nativo di unit test

1. Nel menu **File**, scegliere **Nuovo** > **Progetto**.

     **Visual Studio 2017 e versioni precedenti:** espandere **Modelli**  >  **installati**  >  **Visual C++**  >  **Test**.
     **Visual Studio 2019:** impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca.

     Scegliere il modello **Progetto unit test nativo** o scegliere un qualsiasi altro framework installato. Se si sceglie un altro modello, ad esempio Google Test o Boost.Test, i principi di base sono gli stessi, cambiano però alcuni dettagli.

     In questa procedura dettagliata, il progetto di test viene denominato `NativeRooterTest`.

2. Nel nuovo progetto, controllare **unittest1.cpp**

     ![Progetto di test con TEST&#95;CLASS e TEST&#95;METHOD](../test/media/utecpp2.png)

     Si noti che:

    - Ogni test è definito tramite `TEST_METHOD(YourTestName){...}`.

         Non è necessario scrivere una firma della funzione formale. La firma viene creata dalla macro TEST_METHOD. La macro genera un'istanza a una funzione che restituisce un valore nullo. Viene inoltre generata una funzione statica che restituisce informazioni sul metodo di test. Queste informazioni consentono ad Esplora test di individuare il metodo.

    - I metodi dei test vengono raggruppati in classi usando `TEST_CLASS(YourClassName){...}`.

         Quando si eseguono i test, viene creata un'istanza di ogni classe di test. I metodi di test vengono chiamati in un ordine non specificato. È possibile definire metodi speciali che vengono richiamati prima e dopo ogni modulo, classe, o metodo.

3. Verificare che i test vengano eseguiti in Esplora test:

    1. Inserire il codice di test:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Si noti che la classe `Assert` fornisce diversi metodi statici che è possibile usare per verificare i risultati nei metodi di test.

    2. Nel menu **Test** scegliere **Esegui** > **Tutti i test**.

         Viene eseguita la compilazione e l'esecuzione del test.

         Verrà visualizzato **Esplora test**.

         Il test verrà visualizzato in **Test superati**.

         ![Esplora unit test con un test superato](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a> Creare un progetto DLL

::: moniker range=">=vs-2019"

La procedura seguente illustra come creare un progetto DLL in Visual Studio 2019.

1. Creare un progetto C++ usando la Creazione guidata desktop di **Windows:** fare clic con il pulsante destro del mouse sul nome della **soluzione** in Esplora soluzioni scegliere **Aggiungi**  >  **nuovo progetto.** Impostare **Linguaggio** su C++ e quindi digitare "windows" nella casella di ricerca. Scegliere **Creazione guidata applicazione desktop di Windows** dall'elenco risultati.

     In questa procedura dettagliata, il progetto viene denominato `RootFinder`.

2. Fare clic su **Crea**. Nella finestra di dialogo successiva, in **Tipo di applicazione** scegliere **DLL (libreria a collegamento dinamico)** e selezionare **Esporta simboli**.

     L'opzione **Esporta simboli** genera una semplice macro che è possibile usare per dichiarare i metodi esportati.

     ![Creazione progetto C++ impostata per simboli di esportazione e DLL](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Dichiarare una funzione esportata nel file *con estensione h* principale:

     ![Nuovo progetto di codice DLL e file h con macro API](../test/media/utecpp07.png)

     Il dichiaratore `__declspec(dllexport)` permette ai membri public e protected della classe di essere visibili al di fuori della DLL. Per altre informazioni, vedere [Using dllimport and dllexport in C++ Classes](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Nel file *con estensione cpp* principale, aggiungere il corpo minimo della funzione:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

La procedura seguente illustra come creare un progetto DLL in Visual Studio 2017.

1. Creare un progetto C++ usando il modello **Progetto Win32**.

     In questa procedura dettagliata, il progetto viene denominato `RootFinder`.

2. Selezionare **DLL** ed **Esporta simboli** nella creazione guidata applicazione Win32.

     L'opzione **Esporta simboli** genera una semplice macro che è possibile usare per dichiarare i metodi esportati.

     ![Creazione progetto C++ impostata per simboli di esportazione e DLL](../test/media/utecpp06.png)

3. Dichiarare una funzione esportata nel file *con estensione h* principale:

     ![Nuovo progetto di codice DLL e file h con macro API](../test/media/utecpp07.png)

     Il dichiaratore `__declspec(dllexport)` permette ai membri public e protected della classe di essere visibili al di fuori della DLL. Per altre informazioni, vedere [Using dllimport and dllexport in C++ Classes](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Nel file *con estensione cpp* principale, aggiungere il corpo minimo della funzione:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a> Unire il progetto di test al progetto DLL

1. Aggiungere il progetto DLL ai riferimenti del progetto di test:

   1. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Aggiungi** > **Riferimento**.

   2. Nella finestra di dialogo **Aggiungi riferimento** , selezionare il progetto DLL e scegliere **Aggiungi**.

        ![Proprietà progetto C++ | Aggiungi nuovo riferimento](../test/media/utecpp09.png)

2. Nel file principale *con estensione cpp* dello unit test, includere il file *con estensione h* del codice DLL:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Aggiungere un test di base che usa la funzione esportata:

   ```cpp
   TEST_METHOD(BasicTest)
   {
      CRootFinder rooter;
      Assert::AreEqual(
         // Expected value:
         0.0,
         // Actual value:
         rooter.SquareRoot(0.0),
         // Tolerance:
         0.01,
        // Message:
        L"Basic test failed",
        // Line number - used if there is no PDB file:
        LINE_INFO());
   }
   ```

4. Compilare la soluzione.

    Il nuovo test viene visualizzato in **Esplora test**.

5. In **Esplora test** scegliere Esegui **tutto.**

    ![Esplora unit test &#45; Test di base superato](../test/media/utecpp10.png)

   È stato installato il test e i progetti di codice, e verificato che sia possibile eseguire test che eseguono funzioni nel progetto di codice. Ora è possibile iniziare a scrivere test e codici reali.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Aumentare i test in modo iterativo e renderli superati

1. Aggiungere un nuovo test:

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > È consigliabile non modificare i test che siano stati superati. Al contrario, aggiungere un nuovo test, aggiornare il codice in modo che il test passi e quindi aggiungere un altro test, e così via.
    >
    > Quando gli utenti modificano i requisiti, disabilitare i test che non sono più corretti. Scrivere nuovi test e farli funzionare uno alla volta, nello stesso modo incrementale.

2. Compilare la soluzione e quindi scegliere **Esegui tutto** in **Esplora test**.

     Il nuovo test non riesce.

     ![RangeTest non riuscito](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Verificare che ogni test non venga superato subito dopo averlo scritto. Questo consente di evitare il semplice errore di scrivere un test che riesce sempre.

3. Ottimizzare il codice della DLL in modo che il nuovo test abbia esito positivo:

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
    {
      double result = v;
      double diff = v;
      while (diff > result/1000)
      {
        double oldResult = result;
        result = result - (result*result - v)/(2*result);
        diff = abs (oldResult - result);
      }
      return result;
    }
    ```

4. Compilare la soluzione e quindi in **Esplora test** scegliere **Esegui tutto**.

     Entrambi i test vengono superati.

     ![Esplora unit test &#45; Test intervallo superato](../test/media/utecpp12.png)

    > [!TIP]
    > Sviluppare il codice aggiungendo un test alla volta. Assicurarsi che tutti i test vengano superati dopo ogni iterazione.

## <a name="debug-a-failing-test"></a><a name="debug"></a> Eseguire il debug di un test non riuscito

1. Aggiungere un altro test:

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2. Compilare la soluzione e scegliere **Esegui tutto**.

3. Aprire (o fare doppio clic) sul test non superato.

     L'asserzione fallita viene evidenziata. Il messaggio di errore è visibile nel riquadro dei dettagli di **Esplora test**.

     ![NegativeRangeTests non riuscito](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Per capire perché il test non riesce, scorrere la funzione:

    1. Impostare il punto di interruzione all'inizio della funzione SquareRoot.

    2. Dal menu di scelta rapida del test non superato, scegliere **Esegui debug test selezionati**.

         Quando l'esecuzione si arresta in corrispondenza del punto di interruzione, eseguire il codice un'istruzione alla volta.

5. Inserire il codice nella funzione che si sta sviluppando:

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6. Tutti i test vengono ora superati.

   ![Tutti i test superati](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Se i singoli test non hanno dipendenze che ne impediscono l'esecuzione in qualsiasi ordine, attivare l'esecuzione di test paralleli con lo screenshot del pulsante di attivazione/disattivazione dell'esecuzione dei test in parallelo sulla barra ![ degli strumenti di Esplora test. Quando questo pulsante è selezionato, i test verranno eseguiti in parallelo.](../test/media/ute_parallelicon-small.png) sulla barra degli strumenti. Questo può ridurre notevolmente il tempo impiegato per eseguire tutti i test.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Se i singoli test non hanno dipendenze che ne impediscono l'esecuzione in qualsiasi ordine, attivare l'esecuzione parallela dei test nel menu Impostazioni sulla barra degli strumenti. Questo può ridurre notevolmente il tempo impiegato per eseguire tutti i test.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Eseguire il refactoring del codice senza modificare i test

1. Semplificare il calcolo centrale nella funzione SquareRoot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Compilare la soluzione e scegliere **Esegui tutto**, per assicurarsi che non sia stato introdotto un errore.

    > [!TIP]
    > Un buon set di test d'unità consente di assicurarsi che non siano stati introdotti bug con la modifica del codice.
    >
    > Mantenere il refactoring separato da altre modifiche.

## <a name="next-steps"></a>Passaggi successivi

- **Isolamento.** La maggior parte delle DLL dipende da altri sottosistemi quali database ed altre DLL. Queste altre componenti vengono spesso sviluppate in parallelo. Per permettere l'esecuzione di unit test mentre gli altri componenti non sono ancora disponibili è necessario sostituirli con una simulazione.

- **Test di verifica della compilazione.** È possibile eseguire test sul server di compilazione del team a intervalli predefiniti. Questo assicura che i bug non verranno introdotti quando il lavoro dei diversi membri del team viene integrato.

- **Test di controllo.** È possibile lasciare che alcuni test vengano eseguiti prima che ogni membro del team esegua controllo del codice sorgente. In genere questo è un sottoinsieme del set completo dei test di verifica della compilazione.

   È anche possibile lasciare al chiamante un livello minimo di code coverage.

## <a name="see-also"></a>Vedi anche

- [Aggiungere unit test alle applicazioni C++ esistenti](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Utilizzo di Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Eseguire il debug di codice nativo](../debugger/debugging-native-code.md)
- [Procedura dettagliata: Creazione e uso di una libreria di collegamento dinamico (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importare ed esportare](/cpp/build/importing-and-exporting)
