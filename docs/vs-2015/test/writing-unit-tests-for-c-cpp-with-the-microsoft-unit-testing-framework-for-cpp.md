---
title: Scrittura di unit test per C/C++ con il framework unit test di Microsoft per C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d238b5923c6f1377ec68717c8ed658bc74fe8e6a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695278"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>Scrittura di unit test per C/C++ con il framework di testing unità Microsoft per C++.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, è possibile creare unit test per il codice non gestito scritto in C++. Il codice non gestito è talvolta denominato codice nativo.  
  
 La procedura riportata di seguito contiene le informazioni essenziali utili per iniziare. Nelle sezioni successive sarà fornita una procedura dettagliata in cui verranno descritti più dettagliatamente i passaggi.  
  
### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Per scrivere unit test per una DLL di codice non gestito  
  
1. Usare il modello **Progetto di test nativo** per creare un progetto di Visual Studio separato per i test.  
  
     Il progetto contiene un codice di test di esempio.  
  
2. Rendere la DLL accessibile al progetto di test:  
  
    - `#include` un file `.h` che contiene le dichiarazioni delle funzioni esternamente accessibili della DLL.  
  
         Il file `.h` deve contenere dichiarazioni di funzione contrassegnate da `_declspec(dllimport)`. In alternativa, è possibile esportare i metodi usando un file DEF. Per altre informazioni, vedere [Importazione ed esportazione](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).  
  
         Gli unit test possono accedere solo alle funzioni esportate dalla DLL sottoposta a test.  
  
    - Aggiungere il progetto DLL ai riferimenti del progetto di test:  
  
         In **Proprietà** del progetto di test, espandere **Proprietà comuni**, **Framework e riferimenti**, quindi scegliere **Aggiungi riferimento**.  
  
3. Nel progetto di test, creare le classi e i metodi di test usando le macro TEST e la classe Assert nel modo seguente:  
  
    ```cpp  
    #include "stdafx.h"  
    #include <CppUnitTest.h>  
    #include "..\MyProjectUnderTest\MyCodeUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    TEST_CLASS(TestClassName)  
    {  
    public:  
      TEST_METHOD(TestMethodName)  
      {  
        // Run a function under test here.  
        Assert::AreEqual(expectedValue, actualValue, L"message", LINE_INFO());  
      }  
    }  
    ```  
  
    - `Assert` contiene diverse funzioni statiche che è possibile usare per verificare i risultati di un test.  
  
    - Il parametro `LINE_INFO()` è facoltativo. Nei casi in cui non esiste alcun file PDB, consente al Test Runner di identificare la posizione di un errore.  
  
    - È anche possibile scrivere metodi di impostazione e pulizia dei test. Per altre informazioni, aprire la definizione della macro `TEST_METHOD` e leggere i commenti in CppUnitTest.h.  
  
    - Non è possibile annidare le classi di test.  
  
4. Usare Esplora test per eseguire i test:  
  
    1. Dal menu **Visualizza** scegliere **Altre finestre**, **Esplora test**.  
  
    2. Compilare la soluzione di Visual Studio.  
  
    3. In Esplora test scegliere **Esegui tutto**.  
  
    4. Per analizzare qualsiasi test più dettagliatamente con Esplora test:  
  
        1. Selezionare il nome del test per visualizzare più dettagli, come un messaggio di errore ed una traccia dello stack.  
  
        2. Aprire il nome del test (ad esempio facendo doppio clic) per passare alla posizione dell'errore o del codice di test.  
  
        3. Dal menu di scelta rapida di un test, scegliere **Debug del test selezionato** per eseguire il test nel debugger  
  
## <a name="walkthrough"></a> Procedura dettagliata: Sviluppo di una DLL non gestita con Esplora Test  
 È possibile adattare questa procedura dettagliata per compilare la propria DLL. La procedura principale è la seguente:  
  
1. [Creare un progetto di test nativo](#unitTestProject). I test vengono creati in un progetto separato dalla DLL che si sta sviluppando.  
  
2. [Creare un progetto DLL](#createDllProject). In questa procedura dettagliata viene creato un nuovo file DLL, ma la procedura per testare una DLL esistente è simile.  
  
3. [Definire le funzioni DLL visibili ai test](#coupleProjects).  
  
4. [Aumentare i test iterativamente](#iterate). Si consiglia un ciclo "red-green-refactor", in cui lo sviluppo di codice è condotto dai test.  
  
5. [Debug di test non superati](#debug). È possibile eseguire test in modalità debug.  
  
6. [Effettuare il refactoring mantenendo i test invariati](#refactor). Il refactoring indica il miglioramento della struttura del codice senza modificarne il comportamento esterno. È possibile eseguirla per migliorare prestazioni, estendibilità o leggibilità del codice. Poiché lo scopo non è di modificare il comportamento, non si modificano i test mentre si esegue il refactoring del codice. I test consentono di verificare che non vengano inseriti bug durante il refactoring. È possibile apportare modifiche più facilmente che non senza i test.  
  
7. [Controllo del code coverage](https://msdn.microsoft.com/library/fc8hec9e.aspx). I test d'unità sono particolarmente utili quando eseguono più parti del codice. È possibile individuare quali parti del codice sono state usate dai test.  
  
8. [Unità isolate da risorse esterne](https://msdn.microsoft.com/library/hh549174.aspx). In genere, una DLL dipende da altri componenti del sistema che si sta sviluppando, come altre DLL, i database, o dei sottosistemi remoti. È utile verificare ogni unità in isolamento dalle relative dipendenze. I componenti esterni possono provocare un rallentamento dell'esecuzione dei test. Durante lo sviluppo, gli altri componenti potrebbero non essere completati.  
  
### <a name="unitTestProject"></a> Creare un progetto nativo di unit test  
  
1. Nel menu **File** , scegliere **Nuovo**, **Progetto**.  
  
     Nella finestra di dialogo espandere, **Installato**, **Modelli**, **Visual C++**, **Test**.  
  
     Scegliere il modello **Progetto di test nativo** .  
  
     In questa procedura dettagliata, il progetto di test viene denominato `NativeRooterTest`.  
  
     ![Creazione di un progetto unit test C&#43;&#43;](../test/media/utecpp01.png "UteCpp01")  
  
2. Nel nuovo progetto, controllare **unittest1.cpp**  
  
     ![Progetto di test con TEST&#95;CLASS e TEST&#95;METHOD](../test/media/utecpp2.png "UteCpp2")  
  
     Si noti che:  
  
    - Ogni test è definito tramite `TEST_METHOD(YourTestName){...}`.  
  
         Non è necessario scrivere una firma della funzione formale. La firma viene creata dalla macro TEST_METHOD. La macro genera un'istanza a una funzione che restituisce un valore nullo. Viene inoltre generata una funzione statica che restituisce informazioni sul metodo di test. Queste informazioni consentono ad Esplora test di individuare il metodo.  
  
    - I metodi dei test vengono raggruppati in classi usando `TEST_CLASS(YourClassName){...}`.  
  
         Quando vengono eseguiti i test, viene creata un'istanza di ogni classe di test. I metodi di test vengono chiamati in un ordine non specificato. È possibile definire metodi speciali che vengono richiamati prima e dopo ogni modulo, classe, o metodo.  
  
3. Verificare che i test vengano eseguiti in Esplora test:  
  
    1. Inserire il codice di test:  
  
        ```cpp  
        TEST_METHOD(TestMethod1)  
        {  
        Assert::AreEqual(1,1);  
        }  
        ```  
  
         Si noti che la classe `Assert` fornisce diversi metodi statici che è possibile usare per verificare i risultati nei metodi di test.  
  
    2. Dal menu **Test** , scegliere **Esegui** , **Tutti i test**.  
  
         Viene eseguita la compilazione e l'esecuzione del test.  
  
         Verrà visualizzato Esplora test.  
  
         Il test verrà visualizzato in **Test superati**.  
  
         ![Esplora unit test con un test superato](../test/media/utecpp04.png "UteCpp04")  
  
### <a name="createDllProject"></a> Creare un progetto DLL non gestito  
  
1. Creare un progetto **Visual C++** tramite il modello **Progetto Win32** .  
  
     In questa procedura dettagliata, il progetto viene denominato `RootFinder`.  
  
     ![Creazione di un progetto Win32 C&#43;&#43;](../test/media/utecpp05.png "UteCpp05")  
  
2. Selezionare **DLL** ed **Esporta simboli** nella creazione guidata applicazione Win32.  
  
     L'opzione **Esporta simboli** genera una semplice macro che è possibile usare per dichiarare i metodi esportati.  
  
     ![Creazione guidata progetto C&#43;&#43; impostata per simboli di esportazione e DLL](../test/media/utecpp06.png "UteCpp06")  
  
3. Dichiarare una funzione esportata nel file .h principale:  
  
     ![Nuovo progetto di codice DLL e file h con macro API](../test/media/utecpp07.png "UteCpp07")  
  
     Il dichiaratore `__declspec(dllexport)` permette ai membri public e protected della classe di essere visibili al di fuori della DLL. Per altre informazioni, vedere [Using dllimport and dllexport in C++ Classes](https://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).  
  
4. Nel file .cpp principale, aggiungere il corpo minimo della funzione:  
  
    ```cpp  
    // Find the square root of a number.  
    double CRootFinder::SquareRoot(double v)  
    {  
      return 0.0;  
    }  
    ```  
  
### <a name="coupleProjects"></a> Unire il progetto di test al progetto DLL  
  
1. Aggiungere il progetto DLL ai riferimenti del progetto di test:  
  
   1. Aprire le proprietà del progetto di test e scegliere **Proprietà comuni**, **Framework e riferimenti**.  
  
        ![Proprietà progetto C&#43;&#43; &#45; Framework e riferimenti](../test/media/utecpp08.png "UteCpp08")  
  
   2. Scegliere **Aggiungi nuovo riferimento**.  
  
        Nella finestra di dialogo **Aggiungi riferimento** , selezionare il progetto DLL e scegliere **Aggiungi**.  
  
        ![Proprietà progetto C&#43;&#43; &#45; Aggiungere un nuovo riferimento](../test/media/utecpp09.png "UteCpp09")  
  
2. Nel file principale .cpp delll'unit test, includere il file .h del codice DLL:  
  
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
  
    Il nuovo test viene visualizzato in Esplora test.  
  
5. In Esplora test scegliere **Esegui tutto**.  
  
    ![Esplora unit test &#45; Test di base superato](../test/media/utecpp10.png "UteCpp10")  
  
   È stato installato il test e i progetti di codice, e verificato che sia possibile eseguire test che eseguono funzioni nel progetto di codice. Ora è possibile iniziare a scrivere test e codici reali.  
  
### <a name="iterate"></a> Aumentare i test in maniera iterativa e farli passare  
  
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
    >  Quando gli utenti modificano i requisiti, disabilitare i test che non sono più corretti. Scrivere nuovi test e farli funzionare uno alla volta, nello stesso modo incrementale.  
  
2. Compilare la soluzione e quindi in Esplora test, scegliere **Esegui tutto**.  
  
     Il nuovo test non riesce.  
  
     ![RangeTest non riuscito](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    > Verificare che ogni test non venga superato subito dopo averlo scritto. Questo consente di evitare il semplice errore di scrivere un test che riesce sempre.  
  
3. Aumentare il codice sotto test in modo che il nuovo test passi:  
  
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
  
4. Compilare la soluzione e quindi in Esplora test, scegliere **Esegui tutto**.  
  
     Entrambi i test vengono superati.  
  
     ![Esplora unit test &#45; Test intervallo superato](../test/media/utecpp12.png "UteCpp12")  
  
    > [!TIP]
    > Sviluppare il codice aggiungendo un test alla volta. Assicurarsi che tutti i test vengano superati dopo ogni iterazione.  
  
### <a name="debug"></a> Debug di un test non superato  
  
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
  
     L'asserzione fallita viene evidenziata. Il messaggio di errore è visibile nel riquadro dei dettagli di Esplora test.  
  
     ![NegativeRangeTests non riuscito](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
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
  
     ![Tutti i test superati](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
> [!TIP]
> Se i singoli test non hanno dipendenze che ne impediscono l'esecuzione in qualsiasi ordine, attivare l'esecuzione parallela dei test con l'interruttore ![UTE&#95;parallelicon&#45;small](../test/media/ute-parallelicon-small.png "UTE_parallelicon-small") sulla barra degli strumenti. Questo può ridurre notevolmente il tempo impiegato per eseguire tutti i test.  
  
### <a name="refactor"></a> Eseguire il refactoring del codice senza modificare i test  
  
1. Semplificare il calcolo centrale nella funzione SquareRoot:  
  
    ```  
    // old code:  
    //   result = result - (result*result - v)/(2*result);  
    // new code:  
         result = (result + v/result)/2.0;  
  
    ```  
  
2. Compilare la soluzione e scegliere **Esegui tutto**, per assicurarsi che non sia stato introdotto un errore.  
  
    > [!TIP]
    > Un buon set di test d'unità consente di assicurarsi che non siano stati introdotti bug con la modifica del codice.  
    >   
    >  Mantenere il refactoring separato da altre modifiche.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
- **Isolamento.** La maggior parte delle DLL dipende da altri sottosistemi quali database ed altre DLL. Queste altre componenti vengono spesso sviluppate in parallelo. Per permettere l'esecuzione di unit test mentre gli altri componenti non sono ancora disponibili è necessario sostituirli con una simulazione.  
  
- **Test di verifica della compilazione.** È possibile eseguire test sul server di compilazione del team a intervalli predefiniti. Questo assicura che i bug non verranno introdotti quando il lavoro dei diversi membri del team viene integrato.  
  
- **Test di controllo.** È possibile lasciare che alcuni test vengano eseguiti prima che ogni membro del team esegua controllo del codice sorgente. In genere questo è un sottoinsieme del set completo dei test di verifica della compilazione.  
  
     È anche possibile lasciare al chiamante un livello minimo di code coverage.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di unit test alle applicazioni C++ esistenti](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)   
 [Utilizzo di Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md)   
 [Panoramica sull'interoperabilità sul codice gestito e non gestito](https://msdn.microsoft.com/library/ms973872.aspx)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Procedura dettagliata: Creazione e utilizzo di una libreria a collegamento dinamico (C++)](https://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941)   
 [Importazione ed esportazione](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)
