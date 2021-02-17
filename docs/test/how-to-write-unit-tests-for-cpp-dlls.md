---
title: Scrivere unit test per DLL C++
description: Informazioni sui diversi modi per testare il codice DLL, a seconda che la DLL esporti le funzioni che si desidera testare.
ms.custom: SEO-VS-2020
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 06ad7bd437fca98c7be92a1e12ce31234d876b28
ms.sourcegitcommit: cc8547eb211c43b67b8123d1211b80b5642e3b18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563427"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Scrivere unit test per le DLL C++ in Visual Studio

È possibile eseguire test del codice DLL in modi diversi, a seconda che vengano esportate o meno le funzioni da testare. Scegliere uno dei modi seguenti:

**Gli unit test chiamano solo le funzioni esportate dalla DLL:** aggiungere un progetto di test separato come descritto in [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md). Nel progetto di test aggiungere un riferimento al progetto della DLL.

Passare alla procedura [Per fare riferimento a funzioni della DLL esportate dal progetto di test](#projectRef).

**La DLL è compilata come file con estensione exe:** aggiungere un progetto di test separato. Collegarlo al file oggetto di output.

Passare alla procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

**Gli unit test chiamano funzioni non membro che non vengono esportate dalla dll e la dll può essere compilata come libreria statica:** Modificare il progetto di DLL in modo che venga compilato in un file con *estensione LIB* . Aggiungere un progetto di test separato che fa riferimento al progetto incluso nel test.

Questo approccio presenta il vantaggio di consentire ai test l'uso di membri non esportati, mantenendo i test in un progetto separato.

Passare alla procedura [Per modificare la DLL in una libreria statica](#staticLink).

**Gli unit test devono chiamare funzioni non membro che non vengono esportate e il codice deve essere compilato come dll (Dynamic Link Library):** Aggiungere unit test nello stesso progetto del codice prodotto.

Passare alla procedura [Per aggiungere unit test nello stesso progetto](#sameProject).

## <a name="create-the-tests"></a>Creare i test

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Per modificare la DLL in una libreria statica

- Se i test devono usare membri che non vengono esportati dal progetto DLL e il progetto sottoposto a test viene compilato come libreria dinamica, provare a convertirlo in una libreria statica.

  1. In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto sottoposto a test. Si apre la finestra **Proprietà** del progetto.

  2. Scegliere **proprietà di configurazione**  >  **generale**.

  3. Impostare **Tipo di configurazione** su **Libreria statica (.lib)**.

  Continuare con la procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Per fare riferimento a funzioni della DLL esportate dal progetto di test

- Se il progetto della DLL esporta le funzioni che si vogliono testare, è possibile aggiungere un riferimento al progetto di codice dal progetto di test.

  1. Creare un progetto unit test nativo.

      ::: moniker range="vs-2019"

      1. Nel menu **File**, scegliere **Nuovo** > **Progetto**. Nella finestra di dialogo **Aggiungi un nuovo progetto** impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. Scegliere quindi il modello **Progetto per unit test nativi**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Nel menu **File** scegliere **Nuovo** > **Progetto** > **Visual C++** > **Test** > **Progetto unit test C++**.

      ::: moniker-end

  1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di test e scegliere **Aggiungi** > **Riferimento**.

  1. Selezionare **Progetti** e quindi il progetto da testare.

       Fare clic sul pulsante **Aggiungi**.

  1. Nelle proprietà del progetto di test, aggiungere il percorso del progetto incluso nel test a Directory di inclusione.

       Scegliere **proprietà di configurazione**  >  **directory di VC + +**  >  **Includi directory**.

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Andare a [Scrittura di unit test](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Per collegare i test all'oggetto o a file di libreria

- Se la DLL non Esporta le funzioni che si desidera testare, è possibile aggiungere il file con *estensione obj* o *lib* di output alle dipendenze del progetto di test.

  1. Creare un progetto unit test nativo.

      ::: moniker range="vs-2019"

      1. Nel menu **File**, scegliere **Nuovo** > **Progetto**. Nella finestra di dialogo **Aggiungi un nuovo progetto** impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. Scegliere quindi il modello **Progetto per unit test nativi**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Nel menu **File** scegliere **Nuovo** > **Progetto** > **Visual C++** > **Test** > **Progetto unit test C++**.

      ::: moniker-end

  1. In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto di test.

  1. Scegliere **proprietà di configurazione**  >  **linker**  >  **immettere**  >  **dipendenze aggiuntive**.

       Scegliere **Modifica** e aggiungere i nomi dei file con estensione **obj** o **lib**. Non usare i nomi di percorso completi.

  1. Scegliere **proprietà di configurazione**  >  **linker**  >    >  **directory aggiuntive libreria** generale.

       Scegliere **Modifica** e aggiungere il percorso della directory dei file con estensione **obj** o **lib**. Il percorso è in genere contenuto nella cartella di compilazione del progetto sottoposto a test.

  1. Scegliere **proprietà di configurazione**  >  **directory di VC + +**  >  **Includi directory**.

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Andare a [Scrittura di unit test](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Per aggiungere unit test nello stesso progetto

1. Modificare il codice prodotto delle proprietà del progetto per includere le intestazioni e i file di libreria necessari per gli unit test.

   1. In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto sottoposto a test. Si apre la finestra **Proprietà** del progetto.

   1. Scegliere **proprietà di configurazione**  >  **directory di VC + +**.

   1. Modificare le directory di inclusione e di libreria:

       |Directory|Proprietà|
       |-|-|
       |**Directory di inclusione** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
       |**Directory delle librerie** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Aggiungere un file di unit test C++:

   1. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Aggiungi**  >  **nuovo elemento**.

   1. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare  **file di C++ (. cpp)**, assegnargli un nome appropriato, quindi scegliere **Aggiungi**.

   Andare a [Scrittura di unit test](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Scrivere gli unit test

1. In ogni file di codice dello unit test, aggiungere un'istruzione `#include` per le intestazioni del progetto sottoposto a test.

1. Aggiungere le classi e i metodi di test ai file di codice dello unit test. Ad esempio:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>Eseguire i test

1. Nel menu **Test** scegliere **Finestre** > **Esplora test**.

1. Se non tutti i test sono visibili nella finestra, compilare il progetto di test: fare clic con il pulsante destro del mouse sul nodo in **Esplora soluzioni** e scegliere **Compila** o **ricompila**.

1. In **Esplora test** scegliere **Esegui tutto** oppure selezionare i test specifici che si desidera eseguire. Fare clic con il pulsante destro del mouse su un test per altre opzioni, ad esempio per eseguirlo in modalità debug con i punti di interruzione abilitati.

## <a name="see-also"></a>Vedi anche

- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
- [Informazioni di riferimento sull'API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Eseguire il debug di codice nativo](../debugger/debugging-native-code.md)
- [Procedura dettagliata: Creazione e uso di una libreria di collegamento dinamico (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importare ed esportare](/cpp/build/importing-and-exporting)
- [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)
