---
title: Scrivere un visualizzatore in C# | Microsoft Docs
ms.custom: seodec18
ms.date: 04/12/2019
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a46967d5f46c4f495a07d80e5f73cfc9f9d60c1a
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542633"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procedura dettagliata: scrittura di un visualizzatore in C\#
In questa procedura dettagliata viene descritto come usare C# per creare un visualizzatore semplice che consente di visualizzare il contenuto di una stringa in una finestra di messaggio di Windows Form. Questo semplice visualizzatore di stringhe non è particolarmente utile, ma mostra i passaggi di base che è necessario seguire per creare visualizzatori più utili per altri tipi di dati.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni**dal menu **strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger. Pertanto, il primo passaggio consiste nel creare un progetto di libreria di classi per la DLL.

## <a name="create-a-visualizer-manually"></a>Creazione manuale di un visualizzatore

Per creare un visualizzatore, seguire le attività riportate di seguito.

### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi

1. Creare un nuovo progetto di libreria di classi.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Digitare **CTRL + Q** per aprire la casella di ricerca, **digitare libreria di classi**, scegliere **modelli**, quindi scegliere **crea una nuova libreria di classi (.NET Framework)** . Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro sinistro della finestra di dialogo **nuovo progetto** , in oggetto **visivo C#** , scegliere **.NET Framework**, quindi nel riquadro centrale scegliere Libreria di **classi (.NET Framework)** .
    ::: moniker-end

2. Digitare un nome appropriato per la libreria di classi, ad esempio `MyFirstVisualizer`, quindi fare clic su **Crea** o **OK**.

   Dopo avere creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter usare le classi definite in questa DLL. Prima di aggiungere il riferimento, è tuttavia necessario rinominare alcune classi in modo che abbiano nomi significativi.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Per rinominare Class1.cs e aggiungere Microsoft. VisualStudio. DebuggerVisualizers

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su Class1.cs e scegliere **Rinomina** dal menu di scelta rapida.

2. Modificare il nome da Class1.cs a qualcosa di significativo, ad esempio DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifica automaticamente la dichiarazione di classe in DebuggerSide.cs in modo che corrisponda al nuovo nome file.

3. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **riferimenti** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.

4. Nella scheda **Sfoglia** della finestra di dialogo **Aggiungi riferimento** selezionare **Sfoglia** e individuare Microsoft. VisualStudio. DebuggerVisualizers. dll.

    È possibile trovare la DLL in *\<directory di installazione di Visual studio >* sottodirectory \Common7\IDE\PublicAssemblies. della directory di installazione di Visual Studio.

5. Fare clic su **OK**.

6. In DebuggerSide.cs aggiungere quanto segue alle direttive `using`:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   A questo punto è possibile creare il codice sul lato debugger. Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate. In primo luogo, è necessario modificare la dichiarazione dell'oggetto `DebuggerSide` in modo che erediti dalla classe base `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Per ereditare da DialogDebuggerVisualizer

1. In DebuggerSide.cs passare alla riga di codice seguente:

   ```csharp
   public class DebuggerSide
   ```

2. Modificare il codice in:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` ha un solo metodo astratto, `Show`, di cui è necessario eseguire l'override.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Per eseguire l'override del metodo DialogDebuggerVisualizer.Show

- In `public class DebuggerSide` aggiungere il seguente **metodo:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  Il metodo `Show` contiene il codice per la creazione della finestra di dialogo del visualizzatore o un'altra interfaccia utente e per la visualizzazione delle informazioni passate al visualizzatore dal debugger. Questo codice deve essere aggiunto dallo sviluppatore. A tale scopo, in questa procedura dettagliata verrà usata una finestra di messaggio Windows Form. Per prima cosa, è necessario aggiungere una direttiva Reference e `using` per System. Windows. Forms.

### <a name="to-add-systemwindowsforms"></a>Per aggiungere System.Windows.Forms

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **riferimenti** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.

2. Nella scheda **Sfoglia** della finestra di dialogo **Aggiungi riferimento** selezionare **Sfoglia**e individuare il file System. Windows. Forms. dll.

    È possibile trovare la DLL in *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Fare clic su **OK**.

4. In DebuggerSide.cs aggiungere quanto segue alle direttive `using`:

   ```csharp
   using System.Windows.Forms;
   ```

   A questo punto è necessario aggiungere una sezione di codice per la creazione e la visualizzazione dell'interfaccia utente del visualizzatore. Poiché si tratta del primo visualizzatore, l'interfaccia utente verrà mantenuta semplice e verrà utilizzata una finestra di messaggio.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Per visualizzare l'output del visualizzatore in una finestra di dialogo

1. Nel metodo `Show` aggiungere la riga di codice seguente:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Questo codice di esempio non include la gestione degli errori. In un vero visualizzatore o in un qualsiasi altro tipo di applicazione è consigliabile includere la gestione degli errori.

2. Scegliere **Compila MyFirstVisualizer**dal menu **Compila** . La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

   Il codice sul lato debugger è stato completato. È tuttavia necessario eseguire un altro passaggio, ovvero specificare l'attributo che indica al lato dell'oggetto del debug la raccolta di classi che comprende il visualizzatore.

### <a name="to-add-the-debuggee-side-code"></a>Per aggiungere il codice del lato oggetto del debug

1. Aggiungere il seguente codice attributo a DebuggerSide.cs, dopo le direttive `using` ma prima di `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Scegliere **Compila MyFirstVisualizer**dal menu **Compila** . La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

   A questo punto il visualizzatore è pronto. Se la procedura è stata completata in modo corretto, è possibile compilare il visualizzatore e installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Prima di installare un visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è tuttavia consigliabile testarlo per assicurarsi che funzioni in modo corretto. Di seguito viene descritto come creare un test harness per eseguire il visualizzatore senza installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Per aggiungere un metodo di test per aggiungere il visualizzatore

1. Aggiungere il metodo seguente alla classe `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. Scegliere **Compila MyFirstVisualizer**dal menu **Compila** . La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

   Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore. Per semplicità, si userà un progetto di applicazione console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Per aggiungere un progetto applicazione console alla soluzione

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi**, quindi fare clic su **nuovo progetto**.

    ::: moniker range=">=vs-2019"
    Nella casella di ricerca digitare **app console**, scegliere **modelli**, quindi scegliere **Crea una nuova app console (.NET Framework)** . Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** in **Visual C#** scegliere **Windows Desktop**, quindi nel riquadro centrale scegliere **App console (.NET Framework)** .
    ::: moniker-end

2. Digitare un nome appropriato per la libreria di classi, ad esempio `MyTestConsole`, quindi fare clic su **Crea** o **OK**.

   A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Per aggiungere riferimenti necessari a MyTestConsole

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **MyTestConsole** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.

2. Nella scheda **Sfoglia** della finestra di dialogo **Aggiungi riferimento** scegliere Microsoft. VisualStudio. DebuggerVisualizers. dll.

3. Fare clic su **OK**.

4. Fare clic con il pulsante destro del mouse su **MyTestConsole** e scegliere **Aggiungi riferimento** .

5. Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **progetti** , quindi fare clic su MyFirstVisualizer.

6. Fare clic su **OK**.

   A questo punto verrà aggiunto il codice per completare il test harness.

### <a name="to-add-code-to-mytestconsole"></a>Per aggiungere codice a MyTestConsole

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su Program.cs e scegliere **Rinomina** dal menu di scelta rapida.

2. Modificare il nome da Program.cs a qualcosa di più significativo, ad esempio TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifica automaticamente la dichiarazione di classe in TestConsole.cs in modo che corrisponda al nuovo nome file.

3. In TestConsole.cs aggiungere il codice seguente alle direttive `using`:

   ```csharp
   using MyFirstVisualizer;
   ```

4. Nel metodo `Main` aggiungere il codice seguente:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   A questo punto è possibile eseguire il test del visualizzatore.

### <a name="to-test-the-visualizer"></a>Per eseguire il test del visualizzatore

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **MyTestConsole** e scegliere **Imposta come progetto di avvio** dal menu di scelta rapida.

2. Scegliere **Avvia** dal menu **Debug**.

    Viene avviata l'applicazione console e viene visualizzato il visualizzatore e viene visualizzata la stringa "Hello, World".

   Il visualizzatore è stato compilato e sottoposto a test.

   Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo. Per altre informazioni, vedere [procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Creare un visualizzatore usando il modello di elemento del Visualizzatore

Fino a questo punto, questa procedura dettagliata ha illustrato come creare manualmente un visualizzatore. Questa operazione è stata eseguita come esercizio di formazione. Ora che si è appreso come funziona un visualizzatore semplice, esiste un modo più semplice per crearne uno: usando il modello di elemento del visualizzatore.

Prima di tutto, è necessario creare un nuovo progetto libreria di classi.

### <a name="to-create-a-new-class-library"></a>Per creare una nuova libreria di classi

1. Nel menu **File** scegliere **Nuovo > Progetto**.

2. Nella finestra di dialogo **nuovo progetto** , in **oggetto C#visivo** , selezionare **.NET Framework**.

3. Nel riquadro centrale scegliere Libreria di **classi**.

4. Nella casella **nome** Digitare un nome appropriato per la libreria di classi, ad esempio MySecondVisualizer.

5. Fare clic su **OK**.

   A questo punto è possibile aggiungere un elemento del Visualizzatore:

### <a name="to-add-a-visualizer-item"></a>Per aggiungere un elemento del Visualizzatore

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su MySecondVisualizer.

2. Scegliere **Aggiungi** dal menu di scelta rapida, quindi fare clic su **nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** , in **elementi C# visivi**, selezionare **Visualizzatore debugger**.

4. Nella casella **nome** Digitare un nome appropriato, ad esempio SecondVisualizer.cs.

5. Fare clic su **Aggiungi**.

   Questo è tutto. Esaminare il file SecondVisualizer.cs e visualizzare il codice aggiunto dal modello. Procedere e sperimentare il codice. Ora che si conoscono le nozioni di base, è possibile creare visualizzatori più complessi e utili.

## <a name="see-also"></a>Vedere anche

- [Architettura del visualizzatore](../debugger/visualizer-architecture.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
