---
title: Scrivere un visualizzatore in C# | Microsoft Docs
description: Seguire una procedura dettagliata per creare un semplice visualizzatore in C#. Vengono illustrati i passaggi necessari con e senza usare il modello di elemento Visualizzatore.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 86123ece79f7bbde4f4f91fac657dcc235056c0b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384993"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procedura dettagliata: scrittura di un visualizzatore in C\#

In questa procedura dettagliata viene descritto come usare C# per creare un visualizzatore semplice che consente di visualizzare il contenuto di una stringa in una finestra di messaggio di Windows Form. Questo semplice visualizzatore di stringhe non è particolarmente utile di per sé, ma illustra i passaggi di base da seguire per creare visualizzatori più utili per altri tipi di dati.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, passare al menu **Strumenti** e scegliere **Importa ed esporta impostazioni**. Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger. Pertanto, il primo passaggio consiste nel creare un progetto libreria di classi per la DLL.

## <a name="create-a-visualizer-manually"></a>Creare manualmente un visualizzatore

Seguire le attività seguenti per creare un visualizzatore.

### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi

1. Creare un nuovo progetto Libreria di classi.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Digitare **CTRL+Q per** aprire la casella di ricerca, digitare libreria di classi, scegliere **Modelli,** quindi scegliere Crea una nuova libreria di classi **(.NET Framework).** Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **progetto**. Nel riquadro sinistro **della finestra** di dialogo Nuovo progetto in Visual **C#** scegliere **.NET Framework** e quindi nel riquadro centrale scegliere Libreria di classi **(.NET Framework).**
    ::: moniker-end

2. Digitare un nome appropriato per la libreria di classi, ad esempio `MyFirstVisualizer` , e quindi fare clic su **Crea** o **su OK**.

   Dopo avere creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter usare le classi definite in questa DLL. Prima di aggiungere il riferimento, tuttavia, è necessario rinominare alcune classi in modo che abbia nomi significativi.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Per rinominare Class1.cs e aggiungere Microsoft.VisualStudio.DebuggerVisualizers

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su Class1.cs e **scegliere Rinomina** dal menu di scelta rapida.

2. Modificare il nome da Class1.cs in qualcosa di significativo, ad esempio DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifica automaticamente la dichiarazione di classe in DebuggerSide.cs in modo che corrisponda al nuovo nome file.

3. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su Riferimenti** e scegliere **Aggiungi** riferimento dal menu di scelta rapida.

4. Nella scheda Sfoglia **della** finestra  di dialogo Aggiungi riferimento selezionare **Sfoglia** e individuare il Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    È possibile trovare la DLL nella *\<Visual Studio Install Directory> sottodirectory \Common7\IDE\PublicAssemblies* della directory Visual Studio di installazione di .

5. Fare clic su **OK**.

6. In DebuggerSide.cs aggiungere quanto segue alle `using` direttive :

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   A questo punto è possibile creare il codice sul lato debugger. Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate. In primo luogo, è necessario modificare la dichiarazione `DebuggerSide` dell'oggetto in modo che erediti dalla classe di base `DialogDebuggerVisualizer` .

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

- In `public class DebuggerSide` aggiungere il metodo **seguente:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  Il metodo `Show` contiene il codice per la creazione della finestra di dialogo del visualizzatore o un'altra interfaccia utente e per la visualizzazione delle informazioni passate al visualizzatore dal debugger. Questo codice deve essere aggiunto dallo sviluppatore. A tale scopo, in questa procedura dettagliata verrà usata una finestra di messaggio Windows Form. Prima di tutto, è necessario aggiungere un riferimento `using` e una direttiva per System.Windows.Forms.

### <a name="to-add-systemwindowsforms"></a>Per aggiungere System.Windows.Forms

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su Riferimenti** e scegliere **Aggiungi** riferimento dal menu di scelta rapida.

2. Nella scheda Sfoglia **della** finestra  di dialogo Aggiungi riferimento selezionare **Sfoglia** e individuare il System.Windows.Forms.DLL.

    È possibile trovare la DLL in *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Fare clic su **OK**.

4. In DebuggerSide.cs aggiungere quanto segue alle `using` direttive :

   ```csharp
   using System.Windows.Forms;
   ```

   A questo punto è necessario aggiungere una sezione di codice per la creazione e la visualizzazione dell'interfaccia utente del visualizzatore. Poiché si tratta del primo visualizzatore, l'interfaccia utente sarà semplice e verrà utilizzata una finestra di messaggio.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Per visualizzare l'output del visualizzatore in una finestra di dialogo

1. Nel metodo `Show` aggiungere la riga di codice seguente:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Questo codice di esempio non include la gestione degli errori. In un vero visualizzatore o in un qualsiasi altro tipo di applicazione è consigliabile includere la gestione degli errori.

2. Scegliere **Compila** **MyFirstVisualizer dal** menu Compila . La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

   Il codice sul lato debugger è stato completato. È tuttavia necessario eseguire un altro passaggio, ovvero specificare l'attributo che indica al lato dell'oggetto del debug la raccolta di classi che comprende il visualizzatore.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Per aggiungere il tipo da visualizzare per il codice sul lato oggetto del debug

Nel codice sul lato debugger specificare il tipo da visualizzare (l'origine oggetto) per l'oggetto del debug usando <xref:System.Diagnostics.DebuggerVisualizerAttribute> l'attributo . La `Target` proprietà imposta il tipo da visualizzare.

1. Aggiungere il codice di attributo seguente a DebuggerSide.cs, dopo le `using` direttive ma prima di `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Scegliere **Compila** **MyFirstVisualizer dal** menu Compila . La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

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

2. Scegliere **Compila** **MyFirstVisualizer dal** menu Compila . La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

   Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore. Per semplicità, si userà un progetto applicazione console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Per aggiungere un progetto applicazione console alla soluzione

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi** e quindi fare clic **su Nuovo progetto**.

    ::: moniker range=">=vs-2019"
    Nella casella Di ricerca digitare **app console,** scegliere **Modelli,** quindi scegliere **Crea una nuova app console (.NET Framework).** Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **progetto**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** in **Visual C#** scegliere **Windows Desktop**, quindi nel riquadro centrale scegliere **App console (.NET Framework)**.
    ::: moniker-end

2. Digitare un nome appropriato per la libreria di classi, ad esempio `MyTestConsole` , e quindi fare clic su **Crea** o **su OK**.

   A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Per aggiungere riferimenti necessari a MyTestConsole

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su MyTestConsole** e scegliere **Aggiungi** riferimento dal menu di scelta rapida.

2. Nella finestra **di dialogo** Aggiungi riferimento scegliere la **scheda** Sfoglia Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Fare clic su **OK**.

4. Fare clic con il **pulsante destro del mouse su MyTestConsole** e scegliere di nuovo **Aggiungi** riferimento.

5. Nella finestra **di dialogo Aggiungi** riferimento fare clic sulla scheda **Progetti** e quindi su MyFirstVisualizer.

6. Fare clic su **OK**.

   A questo punto verrà aggiunto il codice per completare il test harness.

### <a name="to-add-code-to-mytestconsole"></a>Per aggiungere codice a MyTestConsole

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su Program.cs e **scegliere Rinomina** dal menu di scelta rapida.

2. Modificare il nome da Program.cs in qualcosa di più significativo, ad esempio TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifica automaticamente la dichiarazione di classe in TestConsole.cs in modo che corrisponda al nuovo nome file.

3. In TestConsole.cs aggiungere il codice seguente alle `using` direttive :

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

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **su MyTestConsole** e scegliere **Imposta come progetto di avvio** dal menu di scelta rapida.

2. Scegliere **Avvia** dal menu **Debug**.

    L'applicazione console viene avviata e viene visualizzato il visualizzatore con la stringa "Hello, World".

   Complimenti. è stato compilato e sottoposto a test.

   Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo. Per altre informazioni, vedere [Procedura: Installare un visualizzatore.](../debugger/how-to-install-a-visualizer.md)

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Creare un visualizzatore usando il modello di elemento Visualizzatore

Fino a questo punto, questa procedura dettagliata ha illustrato come creare manualmente un visualizzatore. Questa operazione è stata eseguita come esercizio di apprendimento. Ora che si conosce il funzionamento di un semplice visualizzatore, è possibile crearne uno in modo più semplice: usando il modello di elemento del visualizzatore.

Prima di tutto, è necessario creare un nuovo progetto di libreria di classi.

### <a name="to-create-a-new-class-library"></a>Per creare una nuova libreria di classi

1. Scegliere **Nuovo** progetto dal menu **File > progetto**.

2. Nella finestra **di dialogo Nuovo** progetto in Visual **C#** selezionare **.NET Framework**.

3. Nel riquadro centrale scegliere **Libreria di classi.**

4. Nella casella **Nome** digitare un nome appropriato per la libreria di classi, ad esempio MySecondVisualizer.

5. Fare clic su **OK**.

   A questo punto, è possibile aggiungervi un elemento del visualizzatore:

### <a name="to-add-a-visualizer-item"></a>Per aggiungere un elemento del visualizzatore

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su MySecondVisualizer.

2. Scegliere Aggiungi dal menu di **scelta** rapida e quindi fare clic su **Nuovo elemento.**

3. Nella finestra **di dialogo Aggiungi nuovo** elemento selezionare Visualizzatore debugger in Elementi di Visual **C#.** 

4. Nella casella **Nome** digitare un nome appropriato, ad esempio SecondVisualizer.cs.

5. Fare clic su **Aggiungi**.

   Non c'è altro da fare. Esaminare il file SecondVisualizer.cs e visualizzare il codice aggiunto automaticamente dal modello. Procedere e sperimentare con il codice. Ora che si conoscono le nozioni di base, è possibile creare visualizzatori più complessi e utili.
::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Architettura del visualizzatore](../debugger/visualizer-architecture.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
