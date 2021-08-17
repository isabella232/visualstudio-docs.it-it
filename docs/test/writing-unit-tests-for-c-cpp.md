---
title: Scrivere unit test per C/C++
description: Scrivere unit test C++ in Visual Studio diversi framework di test, tra cui CTest, Boost.Test e Google Test.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 254d3462403018d1110bedcd2a75cb0d5e6fbc978f9a7ee969d6fc7b7332531e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226688"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Scrivere unit test per C/C++ in Visual Studio

È possibile scrivere ed eseguire unit test C++ usando la finestra **Esplora** test. Funziona esattamente come per altri linguaggi. Per altre informazioni sull'uso di **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Alcune funzionalità, ad esempio Live Unit Testing, i test codificati dell'interfaccia utente e IntelliTest, non sono supportate per C++.

Visual Studio include questi framework di test C++ senza richiedere download aggiuntivi:

- Framework di testing unità Microsoft per C++
- Google Test
- Boost.Test
- CTest

Oltre a usare i framework installati, è possibile scrivere un adattatore di test personalizzato per qualsiasi framework che si vuole usare all'interno Visual Studio. Un adattatore di test consente di integrare unit test nella finestra **Esplora test**. Sono disponibili vari adattatori di terze parti in [Visual Studio Marketplace](https://marketplace.visualstudio.com). Per altre informazioni, vedere [Installare framework di unit test di terze parti.](install-third-party-unit-test-frameworks.md)

**Visual Studio 2017 e versioni successive (Professional ed Enterprise)**

I progetti di unit test C++ supportano [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 e versioni successive (tutte le edizioni)**

- **Google Test Adapter** è incluso come componente predefinito del carico di **lavoro Sviluppo di applicazioni desktop con C++.** Include un modello di progetto che è possibile aggiungere a una soluzione. Usare il **menu aggiungi Project** clic con il pulsante destro del mouse sul nodo della soluzione Esplora soluzioni per aggiungerlo.  Include anche opzioni che è possibile configurare tramite **Strumenti**  >  **Opzioni**. Per altre informazioni, [vedere Procedura: Usare Google Test in Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test è** incluso come componente predefinito del carico di **lavoro Sviluppo di applicazioni desktop con C++.** È integrato con Esplora **test,** ma attualmente non ha un modello di progetto. Deve essere configurato manualmente. Per altre informazioni, [vedere Procedura: Usare Boost.Test in Visual Studio](how-to-use-boost-test-for-cpp.md).

- Il supporto per **CTest** è incluso nel componente **CMake Tools per C++**, che fa parte del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Per altre informazioni, [vedere Procedura: Usare CTest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 e versioni precedenti**

È possibile scaricare le estensioni Google Test adapter e Boost.Test Adapter Visual Studio Marketplace. È possibile trovarli in [Adattatore di test per Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) e [Adattatore](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest)di test per Google Test .

## <a name="basic-test-workflow"></a>Flusso di lavoro di test di base

Le sezioni seguenti illustrano i passaggi di base per iniziare con il testing unità in C++. La configurazione di base è simile sia per i framework Microsoft che Google Test framework. Per Boost.Test è necessario creare manualmente un progetto di test.

::: moniker range=">=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Creare un progetto di test in Visual Studio 2019

I test vengono definiti ed eseguiti all'interno di uno o più progetti di test. I progetti vengono creati nella stessa soluzione del codice da testare. Per aggiungere un nuovo progetto di test a una soluzione esistente, fare clic con il pulsante destro del mouse sul nodo Soluzione in **Esplora soluzioni**. Nel menu a comparsa scegliere **Aggiungi**  >  **nuovo Project**. Impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. La figura seguente mostra i progetti di test disponibili quando sono installati i carichi di lavoro **Sviluppo di applicazioni desktop con C++** e **Sviluppo per la piattaforma UWP**:

![Progetti di test C++ in Visual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Creare un progetto di test in Visual Studio 2017

I test vengono definiti ed eseguiti all'interno di uno o più progetti di test. I progetti vengono creati nella stessa soluzione del codice da testare. Per aggiungere un nuovo progetto di test, fare clic con il pulsante destro del mouse sul nodo Soluzione in **Esplora soluzioni**  >  **scegliere Aggiungi nuovo Project**. Nel riquadro sinistro scegliere test **Visual C++ test.** Scegliere quindi uno dei tipi di progetto dal riquadro centrale. La figura seguente mostra i progetti di test disponibili quando è installato il carico di lavoro **Sviluppo di applicazioni desktop con C++**:

![Progetti di test C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Creare riferimenti ad altri progetti nella soluzione

Per abilitare l'accesso alle funzioni nel progetto in fase di test, aggiungere un riferimento al progetto nel progetto di test. Fare clic con il pulsante destro del mouse sul nodo **del progetto di test Esplora soluzioni** un menu a comparsa. Scegliere **Aggiungi**  >  **riferimento.** Nella finestra di dialogo Aggiungi riferimento scegliere i progetti da testare.

![Aggiungi riferimento](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Eseguire il collegamento a file oggetto o di libreria

Se il codice di test non esporta le funzioni che si vuole testare, è possibile aggiungere i file con estensione obj o lib di output alle dipendenze del progetto di test. Per altre informazioni, vedere [Per collegare i test ai file di oggetto o di libreria.](how-to-use-microsoft-test-framework-for-cpp.md#object_files)

### <a name="add-include-directives-for-header-files"></a>Aggiungere direttive #include per il file di intestazione

Nel file con estensione *cpp* dell'unit test aggiungere quindi una direttiva `#include` per tutti i file di intestazione che dichiarano i tipi e le funzioni da testare. Digitare `#include "`. Verrà attivato IntelliSense per facilitare la scelta. Ripetere per eventuali intestazioni aggiuntive.

![Screenshot dell'Esplora soluzioni che mostra una direttiva #include aggiunta con IntelliSense che evidenzia un file di intestazione per l'inclusione.](media/cpp-add-includes-test-project.png)

Per evitare di dover digitare il percorso completo in ogni istruzione include nel file di origine, è possibile aggiungere le cartelle necessarie in Proprietà di **Project**  >    >  **C/C++**  >  **Directory**  >  di inclusione aggiuntive generali .

### <a name="write-test-methods"></a>Scrivere i metodi di test

> [!NOTE]
> Questa sezione mostra la sintassi per il framework di testing unità Microsoft per C/C++. La documentazione è disponibile in [Informazioni di riferimento sulle API di Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Per la documentazione di Google Test, vedere [Google Test primer](https://github.com/google/googletest/blob/master/docs/primer.md) (Introduzione a Google Test). Per Boost.Test, vedere [Boost Test library: The unit test framework](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Libreria di test Boost: framework di unit test).

Il file *con estensione cpp* nel progetto di test ha una classe stub e un metodo definiti per l'utente. Illustrano un esempio di come scrivere codice di test. Le firme usano le macro TEST_CLASS e TEST_METHOD, che rendono i metodi individuabili dalla finestra **Esplora** test.

![Screenshot della finestra Esplora test che mostra il file di codice unittest1.cpp contenente una classe e un metodo stub usando le macro TEST_CLASS e TEST_METHOD test.](media/cpp-write-test-methods.png)

TEST_CLASS e TEST_METHOD fanno parte del [framework di test nativo Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Esplora test** consente di individuare i metodi di test in altri framework supportati in modo analogo.

TEST_METHOD restituisce void. Per produrre un risultato di test, usare i metodi statici nella classe `Assert` per testare i risultati effettivi rispetto a quanto previsto. Nell'esempio seguente si presuppone che `MyClass` includa un costruttore che accetta `std::string`. È possibile verificare che il costruttore inizializzi la classe come previsto in questo modo:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Nell'esempio precedente, il risultato della chiamata `Assert::AreEqual` determina l'esito positivo o negativo del test. La classe Assert contiene molti altri metodi per il confronto dei risultati previsti con quelli effettivi.

È possibile aggiungere *tratti ai* metodi di test per specificare i proprietari dei test, la priorità e altre informazioni. È quindi possibile usare questi valori per ordinare e raggruppare i test in **Esplora test**. Per altre informazioni, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Eseguire i test

1. Nel menu **Test** scegliere **Finestre** > **Esplora test**. La figura seguente illustra un progetto di test con test non ancora eseguiti.

   ![Esplora test prima di eseguire i test](media/cpp-test-explorer.png)

   > [!NOTE]
   > L'integrazione di CTest con **Esplora test** non è ancora disponibile. Eseguire test CTest dal menu principale di CMake.

1. Se non tutti i test sono visibili nella finestra, compilare il progetto di  test facendo clic con il pulsante destro del mouse sul relativo nodo Esplora soluzioni e scegliendo **Compila** o **Ricompila**.

1. In **Esplora test** scegliere Esegui **tutto** oppure selezionare i test specifici da eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati. Dopo aver eseguito tutti i test, la finestra mostra i test superati e quelli non superati:

![Esplora test dopo l'esecuzione dei test](media/cpp-test-explorer-passed.png)

Per i test non superati, il messaggio include dettagli utili per diagnosticare la causa. Fare clic con il pulsante destro del mouse sul test non riuscito per visualizzare un menu a comparsa. Scegliere **Debug test selezionati per** eseguire la funzione in cui si è verificato l'errore.

Per altre informazioni sull'uso di **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

Per altre informazioni relative agli unit test, vedere [Nozioni di base sugli unit test](unit-test-basics.md)

## <a name="use-codelens"></a>Usare CodeLens

**Visual Studio 2017 e versioni successive (edizioni Professional ed Enterprise)**

[CodeLens consente](../ide/find-code-changes-and-other-history-with-codelens.md) di visualizzare rapidamente lo stato di un unit test senza uscire dall'editor di codice.

È possibile inizializzare CodeLens per un progetto di unit test C++ in uno dei modi seguenti:

- Modificare e compilare la soluzione o il progetto di test.
- Ricompilare la soluzione o il progetto.
- Eseguire i test dalla **finestra Esplora** test.

Dopo l'inizializzazione, è possibile visualizzare le icone di stato dei test sopra ogni unit test.

![Icone CodeLens C++](media/cpp-test-codelens-icons.png)

Fare clic sull'icona per altre informazioni o per eseguire lo unit test o eseguirne il debug:

![Esecuzione e debug in CodeLens C++](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Vedi anche

- [Eseguire unit test del codice](unit-test-your-code.md)
