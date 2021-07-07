---
title: Scrivere un visualizzatore in C# | Microsoft Docs
description: Seguire una procedura dettagliata per creare un semplice visualizzatore in C#. Vengono illustrati i passaggi necessari con e senza usare il modello di elemento Visualizzatore.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
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
ms.openlocfilehash: 47c7fa8eaa5a735f05b338101a1aefe0601e9915
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298283"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procedura dettagliata: scrittura di un visualizzatore in C\#

In questa procedura dettagliata viene descritto come usare C# per creare un visualizzatore semplice Il visualizzatore che verrà creato in questa procedura dettagliata visualizza il contenuto di una stringa usando un Windows Form. Questo semplice visualizzatore di stringhe non è particolarmente utile di per sé, ma illustra i passaggi di base da seguire per creare visualizzatori più utili per altri tipi di dati.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, passare al menu **Strumenti** e scegliere Importa **ed esporta** Impostazioni . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger. Pertanto, il primo passaggio consiste nel creare un progetto libreria di classi per la DLL.

## <a name="create-a-visualizer-manually"></a>Creare manualmente un visualizzatore

Seguire le attività seguenti per creare un visualizzatore.

### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi

* Creare un nuovo progetto Libreria di classi.

    ::: moniker range=">=vs-2019"
    Scegliere **File**  >  **nuovo**  >  **Project**. Nell'elenco a discesa del linguaggio scegliere **C#**. Nella casella di ricerca digitare **libreria di classi** e quindi scegliere Libreria di classi **(.NET Framework)**. Fare clic su **Avanti**. Nella finestra di dialogo visualizzata digitare il nome `MyFirstVisualizer` e quindi fare clic su **Crea**.

    Per il progetto del visualizzatore, assicurarsi di selezionare una .NET Framework di classi e non .NET. Anche se il visualizzatore deve essere .NET Framework, l'app chiamante può essere .NET Core.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **Project**. Nel riquadro sinistro **della finestra** di dialogo Nuovo progetto in Visual **C#** scegliere **.NET Framework** e quindi nel riquadro centrale scegliere Libreria di classi **(.NET Framework).**

    Digitare un nome appropriato per la libreria di classi, ad esempio `MyFirstVisualizer` , e quindi fare clic su **Crea** o **su OK.**
    ::: moniker-end

   Dopo avere creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter usare le classi definite in questa DLL. Prima di aggiungere il riferimento, tuttavia, è necessario rinominare alcune classi in modo che abbia nomi significativi.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Per rinominare Class1.cs e aggiungere Microsoft.VisualStudio.DebuggerVisualizers

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su Class1.cs e **scegliere Rinomina** dal menu di scelta rapida.

2. Modificare il nome da Class1.cs a qualcosa di significativo, ad esempio DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifica automaticamente la dichiarazione di classe in DebuggerSide.cs in modo che corrisponda al nuovo nome file.

3. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su Riferimenti** e scegliere **Aggiungi** riferimento dal menu di scelta rapida.

4. Nella scheda Sfoglia **della** finestra  di dialogo Aggiungi riferimento selezionare **Sfoglia** e trovare il Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    È possibile trovare la DLL nella *\<Visual Studio Install Directory> sottodirectory \Common7\IDE\PublicAssemblies* della directory Visual Studio di installazione di .

5. Fare clic su **OK**.

6. In DebuggerSide.cs aggiungere quanto segue alle `using` direttive :

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   A questo punto è possibile creare il codice sul lato debugger. Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate. In primo luogo, è necessario modificare la dichiarazione `DebuggerSide` dell'oggetto in modo che erediti dalla classe base `DialogDebuggerVisualizer` .

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

  Il metodo `Show` contiene il codice per la creazione della finestra di dialogo del visualizzatore o un'altra interfaccia utente e per la visualizzazione delle informazioni passate al visualizzatore dal debugger. Questo codice deve essere aggiunto dallo sviluppatore. A tale scopo, in questa procedura dettagliata verrà utilizzata una finestra di messaggio Windows Form. Prima di tutto, è necessario aggiungere un riferimento `using` e una direttiva per System.Windows. Forme.

### <a name="to-add-systemwindowsforms"></a>Per aggiungere System.Windows.Forms

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su Riferimenti** e scegliere **Aggiungi** riferimento dal menu di scelta rapida.

2. Nella **scheda** Sfoglia della finestra  di dialogo Aggiungi riferimento selezionare **Sfoglia** e individuare il System.Windows.Forms.DLL.

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

Nel codice sul lato debugger specificare il tipo da visualizzare (origine oggetto) per l'oggetto del debug usando <xref:System.Diagnostics.DebuggerVisualizerAttribute> l'attributo . La `Target` proprietà imposta il tipo da visualizzare.

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

   Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore. Per semplicità, usare un progetto Applicazione console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Per aggiungere un progetto applicazione console alla soluzione

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione, scegliere **Aggiungi** e quindi fare clic su **Nuovo Project**.

    ::: moniker range=">=vs-2019"

    Scegliere **File**  >  **nuovo**  >  **Project**. Nell'elenco a discesa del linguaggio scegliere **C#**. Nella casella di ricerca digitare **app console** e quindi scegliere App **console (.NET Framework)** o **Applicazione console** per .NET. Fare clic su **Avanti**. Nella finestra di dialogo visualizzata digitare il nome `MyTestConsole` e quindi fare clic su **Crea**.

    > [!NOTE]
    > Se si vuole testare facilmente il visualizzatore usando un test harness, creare un'app console .NET Framework personalizzata. È invece possibile creare un'app console .NET, ma il test harness descritto più avanti non è ancora supportato per .NET, quindi è necessario installare il visualizzatore per testarlo. Per questo scenario, creare prima l'app console qui e quindi seguire i passaggi descritti in Aggiungere un oggetto dati sul lato oggetto [di debug](#add-a-debuggee-side-data-object).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **Project**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** in **Visual C#** scegliere **Windows Desktop**, quindi nel riquadro centrale scegliere **App console (.NET Framework)**.

    Digitare un nome appropriato per la libreria di classi, ad esempio `MyTestConsole` , e quindi fare clic su **OK.**
    ::: moniker-end

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

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyTestConsole** e **scegliere** Imposta come Project dal menu di scelta rapida.

2. Scegliere **Avvia** dal menu **Debug**.

    L'applicazione console viene avviata e viene visualizzato il visualizzatore con la stringa "Hello, World".

   Complimenti. Il primo visualizzatore è stato appena compilato e testato.

   Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo. Per altre informazioni, vedere [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Aggiungere un oggetto dati sul lato oggetto del debug

In questa sezione si passa `System.String` dall'oggetto dati a un oggetto dati personalizzato.  

1. Scegliere **File**  >  **nuovo**  >  **Project**. Nell'elenco a discesa del linguaggio scegliere **C#**. Nella casella di ricerca digitare **libreria** di classi e quindi scegliere Libreria di classi **(.NET Framework)** o Libreria di **classi** per .NET Standard.

   >[!NOTE]
   >Se si usa un'app console .NET Framework test, assicurarsi di creare un progetto .NET Framework libreria di classi.

1. Fare clic su **Avanti**. Nella finestra di dialogo visualizzata digitare il nome `MyDataObject` e quindi fare clic su **Crea**.

1. (.NET Standard solo libreria di classi) In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e **scegliere Project File**. Modificare il `<TargetFramework>` valore in `netstandard2.0` .

1. `MyDataObject`All'interno dello spazio dei nomi sostituire il codice predefinito con il codice seguente.

   ```csharp
   [Serializable] 
   public class CustomDataObject
   {
      public CustomDataObject()
      {
         this.MyData = "MyTestData";
      }
      public string MyData { get; set; }
   }
   ```

   Per un visualizzatore di sola lettura, ad esempio in questo esempio, non è necessario implementare i metodi di [VisualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource).

   Aggiornare quindi il progetto MyFirstVisualizer per usare il nuovo oggetto dati.

1. Nel Esplora soluzioni nel progetto MyFirstVisualizer fare clic con il pulsante destro del mouse sul nodo **Riferimenti** e scegliere **Aggiungi riferimento**.

1. In **Progetti** selezionare il **progetto MyDataObject.**

1. Nel codice dell'attributo di DebuggerSide.cs aggiornare il valore target, modificando `System.String` in `MyDataObject.CustomDataObject` .

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. Nel progetto MyFirstVisualizer sostituire il codice per il `Show` metodo con il codice seguente.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   Il codice precedente usa una proprietà dell'oggetto dati da visualizzare nel titolo del form.

   Aggiornare quindi l'app console per usare l'oggetto dati personalizzato.

1. Nel Esplora soluzioni nel progetto MyTestConsole fare clic con  il pulsante destro del mouse sul nodo **Riferimenti** o Dipendenze e aggiungere un riferimento al progetto a `MyDataObject` .

1. In Program.cs sostituire il codice nel `Main` metodo con il codice seguente.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (app console .NET) Racchiudere la chiamata `TestShowVisualizer` a in un'istruzione try-catch, poiché l'test harness non è supportato.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   Il debugger richiede un riferimento al visualizzatore. Un modo per mantenere il riferimento è mantenere il codice precedente sul posto.

1. Per un.NET Framework app console, è possibile eseguire il test harness (premere **F5)** oppure seguire le istruzioni in [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).

   Se si esegue l'app usando il test harness, l'app mostra il Windows Form.

1. Per un'app console .NET, copiare e nelle cartelle descritte `MyFirstVisualizer.dll` `MyDataObject.dll` in [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).

1. Dopo aver installato il visualizzatore, impostare un punto di interruzione, eseguire l'app console e passare il mouse su `customDataObject` . Se tutto è configurato correttamente, verrà visualizzata l'icona a forma di lente di ingrandimento ![VisualizzatoreIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del visualizzatore").

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Icona della lente di ingrandimento del visualizzatore.":::

   Quando si sceglie **MyFirstVisualizer** dalla lente di ingrandimento, nel titolo verrà visualizzato il modulo con il testo dell'oggetto dati.

   ![Visualizzatore che mostra un Windows modulo](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Creare un visualizzatore usando il modello di elemento Visualizzatore

Finora, questa procedura dettagliata ha illustrato come creare manualmente un visualizzatore. Questa operazione è stata eseguita come esercizio di apprendimento. Ora che si conosce il funzionamento di un semplice visualizzatore, è possibile crearne uno in modo più semplice: usando il modello di elemento del visualizzatore.

Prima di tutto, è necessario creare un nuovo progetto di libreria di classi.

### <a name="to-create-a-new-class-library"></a>Per creare una nuova libreria di classi

1. Scegliere **Nuovo** dal menu File **> Project**.

2. Nella finestra **di dialogo Project,** in **Visual C#** selezionare **.NET Framework**.

3. Nel riquadro centrale scegliere **Libreria di classi**.

4. Nella casella **Nome** digitare un nome appropriato per la libreria di classi, ad esempio MySecondVisualizer.

5. Fare clic su **OK**.

   A questo punto, è possibile aggiungervi un elemento del visualizzatore:

### <a name="to-add-a-visualizer-item"></a>Per aggiungere un elemento del visualizzatore

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su MySecondVisualizer.

2. Scegliere Aggiungi dal menu di scelta **rapida** e quindi fare clic su **Nuovo elemento.**

3. Nella finestra **di dialogo Aggiungi nuovo elemento** in Elementi di Visual **C#** selezionare **Visualizzatore debugger**.

4. Nella casella **Nome** digitare un nome appropriato, ad esempio SecondVisualizer.cs.

5. Fare clic su **Aggiungi**.

   Questo è tutto ciò che c'è da fare. Esaminare il file SecondVisualizer.cs e visualizzare il codice aggiunto automaticamente dal modello. Procedere e sperimentare con il codice. Ora che si conoscono le nozioni di base, è possibile creare visualizzatori più complessi e utili.
::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Architettura del visualizzatore](../debugger/visualizer-architecture.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
