---
title: Scrivere unit test per DLL C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279280"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Scrivere unit test per le DLL C++ in Visual Studio

È possibile eseguire test del codice DLL in modi diversi, a seconda che vengano esportate o meno le funzioni da testare. Scegliere uno dei modi seguenti:

**Gli unit test chiamano solo le funzioni esportate dalla DLL:** aggiungere un progetto di test separato come descritto in [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md). Nel progetto di test aggiungere un riferimento al progetto della DLL.

Passare alla procedura [Per fare riferimento a funzioni della DLL esportate dal progetto di test](#projectRef).

**La DLL è compilata come file con estensione exe:** aggiungere un progetto di test separato. Collegarlo al file oggetto di output.

Passare alla procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

**Gli unit test chiamano funzioni non membro che non vengono esportate dalla DLL e la DLL può essere compilata come libreria statica:** modificare il progetto della DLL in modo che venga compilato in un file *LIB*. Aggiungere un progetto di test separato che fa riferimento al progetto incluso nel test.

Questo approccio presenta il vantaggio di consentire ai test l'uso di membri non esportati, mantenendo i test in un progetto separato.

Passare alla procedura [Per modificare la DLL in una libreria statica](#staticLink).

**Gli unit test devono chiamare funzioni non membro che non vengono esportate e il codice deve essere compilato come DLL (libreria di collegamento dinamico):** aggiungere gli unit test nello stesso progetto del codice prodotto.

Passare alla procedura [Per aggiungere unit test nello stesso progetto](#sameProject).

## <a name="create-the-tests"></a>Creare i test

### <a name="staticLink"></a> Per modificare la DLL in una libreria statica

- Se i test devono usare membri che non vengono esportati dal progetto della DLL e il progetto sottoposto al test viene compilato come libreria dinamica, può essere utile convertirlo in una libreria statica.

  1. In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto sottoposto a test. Si apre la finestra **Proprietà** del progetto.

  2. Scegliere **Proprietà di configurazione** > **Generale**.

  3. Impostare **Tipo di configurazione** su **Libreria statica (.lib)** .

  Continuare con la procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

### <a name="projectRef"></a> Per fare riferimento a funzioni della DLL esportate dal progetto di test

- Se il progetto della DLL esporta le funzioni che si vogliono testare, è possibile aggiungere un riferimento al progetto di codice dal progetto di test.

  1. Creare un progetto unit test nativo.

      ::: moniker range="vs-2019"

      1. Nel menu **File** scegliere **Nuovo** > **Progetto**. Nella finestra di dialogo **Aggiungi un nuovo progetto** impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. Scegliere quindi il modello **Progetto per unit test nativi**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Nel menu **file** scegliere **nuovo** > **progetto** > **Visual C++**  > **test** >  **C++ progetto unit test**.

      ::: moniker-end

  1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di test e scegliere **Aggiungi** > **Riferimento**.

  1. Selezionare **Progetti** e quindi il progetto da testare.

       Fare clic sul pulsante **Aggiungi**.

  1. Nelle proprietà del progetto di test, aggiungere il percorso del progetto incluso nel test a Directory di inclusione.

       Scegliere **Proprietà di configurazione** > **Directory di VC++**  > **Directory di inclusione**.

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Andare a [Scrittura di unit test](#addTests).

### <a name="objectRef"></a> Per collegare i test all'oggetto o a file di libreria

- Se la DLL non esporta le funzioni che si vuole testare, è possibile aggiungere il file con estensione *obj* o *lib* di output alle dipendenze del progetto di test.

  1. Creare un progetto unit test nativo.

      ::: moniker range="vs-2019"

      1. Nel menu **File** scegliere **Nuovo** > **Progetto**. Nella finestra di dialogo **Aggiungi un nuovo progetto** impostare **Linguaggio** su C++ e digitare "test" nella casella di ricerca. Scegliere quindi il modello **Progetto per unit test nativi**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. Nel menu **file** scegliere **nuovo** > **progetto** > **Visual C++**  > **test** >  **C++ progetto unit test**.

      ::: moniker-end

  2. In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto di test.

  3. Scegliere **Proprietà di configurazione** > **Linker** > **Input** > **Dipendenze aggiuntive**.

       Scegliere **Modifica** e aggiungere i nomi dei file con estensione **obj** o **lib**. Non usare nomi di percorso completo.

  4. Scegliere **Proprietà di configurazione** > **Linker** > **Generale** > **Directory librerie aggiuntive**.

       Scegliere **Modifica** e aggiungere il percorso della directory dei file con estensione **obj** o **lib**. Il percorso è in genere contenuto nella cartella di compilazione del progetto sottoposto a test.

  5. Scegliere **Proprietà di configurazione** > **Directory di VC++**  > **Directory di inclusione**.

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Andare a [Scrittura di unit test](#addTests).

### <a name="sameProject"></a> Per aggiungere unit test nello stesso progetto

1. Modificare il codice prodotto delle proprietà del progetto per includere le intestazioni e i file di libreria necessari per gli unit test.

   1. In **Esplora soluzioni** scegliere **Proprietà** dal menu di scelta rapida del progetto sottoposto a test. Si apre la finestra **Proprietà** del progetto.

   2. Scegliere **Proprietà di configurazione** > **Directory di VC++** .

   3. Modificare le directory di inclusione e di libreria:

       |Directory|Proprietà|
       |-|-|
       |**Directory di inclusione** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Directory delle librerie** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Aggiungere un file di unit test C++:

   - In **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo elemento** > **Unit Test C++** dal menu di scelta rapida del progetto.

   Andare a [Scrittura di unit test](#addTests).

## <a name="addTests"></a> Scrivere gli unit test

1. In ogni file di codice dello unit test, aggiungere un'istruzione `#include` per le intestazioni del progetto sottoposto a test.

2. Aggiungere le classi e i metodi di test ai file di codice dello unit test. Ad esempio:

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

1. Se non è visibile alcun test nella finestra, compilare il progetto di test facendo clic con il pulsante destro del mouse sul relativo nodo in **Esplora soluzioni** e scegliendo **Compila** o **Ricompila**.

1. In **Esplora test** scegliere **Esegui tutto** o selezionare i test specifici da eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati.

## <a name="see-also"></a>Vedere anche

- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)
- [Informazioni di riferimento sulle API di Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Eseguire il debug di codice nativo](../debugger/debugging-native-code.md)
- [Procedura dettagliata: Creare e usare la propria libreria a collegamento dinamico (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importare ed esportare](/cpp/build/importing-and-exporting)
- [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)
