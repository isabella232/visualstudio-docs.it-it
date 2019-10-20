---
title: Esecuzione di unit test delle applicazioni C++ esistenti con Esplora test | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 34d1918522711f3070cf6988a83ebdbd1e80b2f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659574"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Testing unità delle applicazioni C++ esistenti con Esplora test
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È consigliabile, prima di modificare un'applicazione esistente, assicurarsi di avere una buona copertura con unit test. Questo permette di avere la certezza che le modifiche non abbiano introdotto bug. Se l'applicazione non dispone di unit test, si possono aggiungere usando le tecniche illustrate in questo argomento. In questo argomento viene descritto come aggiungere unit test per codice esistente in Visual C++, partendo dalla decisione di come verificare il codice per la creazione, la scrittura e infine eseguire i test.

## <a name="deciding-how-to-test-your-code"></a>Decidere come testare il codice
 Aprire un progetto C++ esistente e controllarlo per decidere come si desidera aggiungere uno unit test. È possibile usare alcuni strumenti di modellazione, che consentono di visualizzare dipendenze nel codice e consentono di capire come le parti interagiscono. Per altre informazioni, vedere [Visualizzare il codice](../modeling/visualize-code.md).

 È consigliabile separare le modifiche in piccole attività. Prima di ogni piccola modifica, scrivere uno unit test per gli aspetti del comportamento che rimarranno invariati. Questi test continueranno a essere superati dopo avere apportato la modifica. Ad esempio, se si prevede di modificare una funzione di ordinamento in modo che ordini un elenco di persone in base al cognome anziché al nome, è possibile scrivere uno unit test che verifica i nomi in input visualizzati nell'output. Dopo avere apportato la modifica, è possibile aggiungere nuovi unit test per un nuovo comportamento.

 Se è possibile, molti o tutti gli unit test dovrebbero usare solo funzioni esportate. Ma se si modifica solo una piccola parte dell'applicazione, potrebbe essere preferibile usare funzioni che non vengono esportate. Ad esempio, è possibile che i test richiamino funzioni interne o test che impostano e ottengono valori da variabili interne.

 Esistono diversi modi per verificare il codice prodotto, a seconda che si espongano o meno le interfacce che si desidera testare. Scegliere uno dei modi seguenti:

 **Gli unit test useranno solo le funzioni esportate dal codice sottoposto a test:** Aggiungere un progetto di test separato. Nel progetto di test, aggiungere un riferimento al progetto incluso nel test.

 Passare alla procedura [Per fare riferimento a funzioni esportate dal progetto di test](#projectRef).

 **Il codice sottoposto a test viene compilato come file con estensione exe:** Aggiungere un progetto di test separato. Collegarlo al file oggetto di output.

 Passare alla procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

 **Gli unit test devono usare funzioni e dati privati e il codice sottoposto a test può essere compilato come libreria statica:** Modificare il progetto sottoposto a test in modo che venga compilato in un file con estensione LIB. Aggiungere un progetto di test separato che fa riferimento al progetto incluso nel test.

 Questo approccio presenta il vantaggio di consentire ai test l'utilizzo di membri privati, mantenendoli tuttavia in un progetto separato. Tuttavia, potrebbe non essere appropriato per alcune applicazioni in cui è necessario usare una libreria a collegamento dinamico (.dll).

 Passare alla procedura [Per modificare il codice sottoposto a test per una libreria statica](#staticLink).

 **Gli unit test devono usare funzioni e dati privati e il codice deve essere compilato come dll (Dynamic Link Library):** Aggiungere unit test nello stesso progetto del codice prodotto.

 Passare alla procedura [Per aggiungere unit test nello stesso progetto](#sameProject).

## <a name="creating-the-tests"></a>Creazione dei test

### <a name="staticLink"></a> Per modificare il codice sottoposto a test in una libreria statica

- Se i test devono usare membri che non vengono esportati da un progetto incluso nel test e il progetto incluso nel test viene compilato come una libreria dinamica, considerare la possibilità di convertirlo in una libreria statica.

  1. In Esplora soluzioni scegliere **Proprietà** dal menu di scelta rapida del progetto sottoposto a test. Verrà visualizzata la finestra delle proprietà del progetto.

  2. Scegliere **Proprietà di configurazione**, **Generale**.

  3. Impostare **Tipo di configurazione** su **Libreria statica (.lib)** .

  Continuare con la procedura [Per collegare i test all'oggetto o ai file di libreria](#objectRef).

### <a name="projectRef"></a> Per fare riferimento a funzioni esportate dal progetto di test

- Se un progetto incluso nel test esporta le funzioni che si vogliono testare, è possibile aggiungere un riferimento al progetto di codice dal progetto di test.

  1. Creare un progetto di test C++.

      1. Nel menu **File** scegliere **Nuovo**, **Progetto**, **Progetto di test Visual C++** , **Progetto unit test C++** .

  2. In Esplora soluzioni scegliere **Riferimenti** dal menu di scelta rapida del progetto di test. Verrà visualizzata la finestra delle proprietà del progetto.

  3. Selezionare **Proprietà comuni**, **Framework e riferimenti** e quindi scegliere il pulsante **Aggiungi nuovo riferimento**.

  4. Selezionare **Progetti** e quindi il progetto da testare.

       Scegliere il pulsante **Aggiungi** .

  5. Nelle proprietà del progetto di test, aggiungere il percorso del progetto incluso nel test a Directory di inclusione.

       Scegliere **Proprietà di configurazione**, **Cartelle VC++** , **Directory di inclusione**.

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Passare a [Scrittura di unit test](#addTests).

### <a name="objectRef"></a> Per collegare i test all'oggetto o a file di libreria

- Se il codice sottoposto a test non esporta le funzioni che si intende testare, è possibile aggiungere il file con estensione **.obj** o **.lib** di output alle dipendenze del progetto di test.

  1. Creare un progetto di test C++.

      1. Nel menu **File** scegliere **Nuovo**, **Progetto**, **Progetto di test Visual C++** , **Progetto unit test C++** .

  2. In Esplora soluzioni scegliere **Proprietà** dal menu di scelta rapida del progetto di test. Verrà visualizzata la finestra delle proprietà del progetto.

  3. Scegliere **Proprietà di configurazione**, **Linker**, **Input**, **Dipendenze aggiuntive**.

       Scegliere **Modifica** e aggiungere i nomi dei file con estensione **obj** o **lib**. Non usare nomi di percorso completo.

  4. Scegliere **Proprietà di configurazione**, **Linker**, **Generale**, **Directory librerie aggiuntive**.

       Scegliere **Modifica** e aggiungere il percorso della directory dei file con estensione **obj** o **lib**. Il percorso è in genere contenuto nella cartella di compilazione del progetto sottoposto a test.

  5. Scegliere **Proprietà di configurazione**, **Cartelle VC++** , **Directory di inclusione**.

       Scegliere **Modifica** e quindi aggiungere la directory dell'intestazione del progetto sottoposto a test.

  Passare a [Scrittura di unit test](#addTests).

### <a name="sameProject"></a> Per aggiungere unit test nello stesso progetto

1. Modificare il codice prodotto delle proprietà del progetto per includere le intestazioni e i file di libreria necessari per gli unit test.

   1. In Esplora soluzioni, dal menu di scelta rapida del progetto incluso nel test, scegliere Proprietà. Verrà visualizzata la finestra delle proprietà del progetto.

   2. Scegliere **Proprietà di configurazione**, **Directory di VC++** .

   3. Modificare le directory di inclusione e di libreria:

       |||
       |-|-|
       |**Directory di inclusione**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Directory delle librerie**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Aggiungere un file di unit test C++:

   - In Esplora soluzioni scegliere **Aggiungi**, **Nuovo elemento** dal menu di scelta rapida del progetto e quindi **Unit test di C++** .

   Passare a [Scrittura di unit test](#addTests).

## <a name="addTests"></a> Scrittura di unit test

1. In ogni file di codice dello unit test, aggiungere un'istruzione `#include` per le intestazioni del progetto sottoposto a test.

2. Aggiungere le classi e i metodi di test ai file di codice dello unit test. Esempio:

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

   Per altre informazioni, vedere [Testing unità di codice nativo con Esplora test](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c).

## <a name="run-the-tests"></a>Eseguire i test

1. Dal menu **Visualizza** scegliere **Altre finestre**, **Esplora test**.

2. In Esplora test scegliere **Esegui tutto**.

   Per altre informazioni, vedere [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md).
