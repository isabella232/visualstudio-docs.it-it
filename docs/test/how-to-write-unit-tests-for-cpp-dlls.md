---
title: Scrivere unit test per DLL C++
description: Informazioni sui diversi modi per testare il codice DLL, a seconda se la DLL esporta le funzioni da testare.
ms.custom: SEO-VS-2020
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 9918342069b6e60ca4f91df87e7e18e1b405f9870968a2a8f63c5bb580a35199
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409007"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Scrivere unit test per le DLL C++ in Visual Studio

È possibile eseguire test del codice DLL in modi diversi, a seconda che vengano esportate o meno le funzioni da testare. Scegliere uno dei modi seguenti:

**Gli unit test chiamano solo le funzioni esportate dalla DLL:** aggiungere un progetto di test separato come descritto in [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md). Nel progetto di test aggiungere un riferimento al progetto della DLL.

Passare alla procedura [Per fare riferimento a funzioni della DLL esportate dal progetto di test](#projectRef).

**La DLL è compilata come file con estensione exe:** aggiungere un progetto di test separato. Collegarlo al file oggetto di output.

Passare alla procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

Gli unit test chiamano funzioni non membro che non vengono esportate dalla DLL e la DLL può essere compilata **come libreria statica:** Modificare il progetto DLL in modo che sia compilato in un file *con estensione lib.* Aggiungere un progetto di test separato che fa riferimento al progetto incluso nel test.

Questo approccio presenta il vantaggio di consentire ai test l'uso di membri non esportati, mantenendo i test in un progetto separato.

Passare alla procedura [Per modificare la DLL in una libreria statica](#staticLink).

Gli unit test devono chiamare funzioni non membro che non vengono esportate e il codice deve essere compilato come **libreria a collegamento dinamico (DLL):** Aggiungere unit test nello stesso progetto del codice del prodotto.

Passare alla procedura [Per aggiungere unit test nello stesso progetto](#sameProject).

## <a name="create-the-tests"></a>Creare i test

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Per modificare la DLL in una libreria statica

- Se i test devono usare membri non esportati dal progetto DLL e il progetto sotto test viene compilato come libreria dinamica, provare a convertirlo in una libreria statica.

  1. In **Esplora soluzioni** scegliere Proprietà dal menu di scelta rapida del progetto in **fase di test.** Si apre la finestra **Proprietà** del progetto.

  2. Scegliere **Proprietà di configurazione**  >  **Generale**.

  3. Impostare **Tipo di configurazione** su **Libreria statica (.lib)**.

  Continuare con la procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Per fare riferimento a funzioni della DLL esportate dal progetto di test

- Se il progetto della DLL esporta le funzioni che si vogliono testare, è possibile aggiungere un riferimento al progetto di codice dal progetto di test.

  1. Creare un progetto unit test nativo.

      ::: moniker range=">=vs-2019"

      1. Nel menu **File**, scegliere **Nuovo** > **Progetto**. Nella finestra di dialogo **Aggiungi un nuovo progetto** impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. Scegliere quindi il modello **Progetto per unit test nativi**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Scegliere **Nuovo** dal  menu File Project >  > **Visual C++** > **Test** > **unit test C++ Project**.

      ::: moniker-end

  1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di test e scegliere **Aggiungi** > **Riferimento**.

  1. Selezionare **Progetti** e quindi il progetto da testare.

       Fare clic sul pulsante **Aggiungi**.

  1. Nelle proprietà del progetto di test, aggiungere il percorso del progetto incluso nel test a Directory di inclusione.

       Scegliere **Proprietà di configurazione VC++** directory  >  **di**  >  **inclusione** directory .

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Andare a [Scrittura di unit test](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Per collegare i test all'oggetto o a file di libreria

- Se la DLL non esporta le funzioni da testare, è possibile aggiungere il file *obj* o *lib* di output alle dipendenze del progetto di test.

  1. Creare un progetto unit test nativo.

      ::: moniker range=">=vs-2019"

      1. Nel menu **File**, scegliere **Nuovo** > **Progetto**. Nella finestra di dialogo **Aggiungi un nuovo progetto** impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. Scegliere quindi il modello **Progetto per unit test nativi**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Scegliere **Nuovo** dal  menu File Project >  > **Visual C++** > **Test** > **unit test C++ Project**.

      ::: moniker-end

  1. In **Esplora soluzioni** scegliere Proprietà dal menu di scelta rapida del **progetto di** test.

  1. Scegliere **Proprietà di configurazione**- Input  >    >    >  **dipendenze aggiuntive del linker**.

       Scegliere **Modifica** e aggiungere i nomi dei file con estensione **obj** o **lib**. Non usare i nomi di percorso completi.

  1. Scegliere **Configuration Properties**  >  **Linker**  >  **General**  >  Additional Library Directories (Directory **librerie aggiuntive generali del linker Proprietà di configurazione).**

       Scegliere **Modifica** e aggiungere il percorso della directory dei file con estensione **obj** o **lib**. Il percorso è in genere contenuto nella cartella di compilazione del progetto sottoposto a test.

  1. Scegliere **Proprietà di configurazione VC++** directory  >  **di**  >  **inclusione** directory .

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Andare a [Scrittura di unit test](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Per aggiungere unit test nello stesso progetto

1. Modificare il codice prodotto delle proprietà del progetto per includere le intestazioni e i file di libreria necessari per gli unit test.

   1. In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto sottoposto a test. Si apre la finestra **Proprietà** del progetto.

   1. Scegliere **Proprietà di configurazione VC++**  >  **directory**.

   1. Modificare le directory di inclusione e di libreria:

       |Directory|Proprietà|
       |-|-|
       |**Directory di inclusione** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
       |**Directory delle librerie** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Aggiungere un file di unit test C++:

   1. Fare clic con il pulsante destro del mouse sul **nodo Esplora soluzioni** progetto e scegliere **Aggiungi**  >  **nuovo elemento**.

   1. Nella finestra **di dialogo Aggiungi nuovo** elemento selezionare File  **C++ (con estensione cpp),** assegnargli un nome appropriato e quindi scegliere **Aggiungi**.

   Andare a [Scrittura di unit test](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Scrivere gli unit test

1. In ogni file di codice dello unit test, aggiungere un'istruzione `#include` per le intestazioni del progetto sottoposto a test.

1. Aggiungere le classi e i metodi di test ai file di codice dello unit test. Esempio:

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

1. Se non tutti i test sono visibili nella finestra, compilare il progetto di test: fare clic con il pulsante destro del mouse sul nodo in Esplora soluzioni e scegliere **Compila** **o** **Ricompila**.

1. In **Esplora test** scegliere Esegui **tutto** oppure selezionare i test specifici da eseguire. Fare clic con il pulsante destro del mouse su un test per altre opzioni, ad esempio per eseguirlo in modalità di debug con punti di interruzione abilitati.

## <a name="see-also"></a>Vedi anche

- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
- [Informazioni di riferimento sulle API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Eseguire il debug di codice nativo](../debugger/debugging-native-code.md)
- [Procedura dettagliata: Creazione e uso di una libreria di collegamento dinamico (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importare ed esportare](/cpp/build/importing-and-exporting)
- [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)
