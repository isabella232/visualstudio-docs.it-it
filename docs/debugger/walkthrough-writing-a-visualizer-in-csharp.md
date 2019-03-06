---
title: Scrivere un visualizzatore in C# | Microsoft Docs
ms.custom: seodec18
ms.date: 08/01/2018
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
ms.openlocfilehash: 45c80500e216041a444b1f6232d8c939132e413d
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323371"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procedura dettagliata: scrittura di un visualizzatore in C\#
In questa procedura dettagliata viene descritto come usare C# per creare un visualizzatore semplice che consente di visualizzare il contenuto di una stringa in una finestra di messaggio di Windows Form. Questo visualizzatore semplice di stringhe non è particolarmente utile di per sé, ma mostra i passaggi di base che è necessario seguire per creare più utili visualizzatori per altri tipi di dati.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, vedere il **strumenti** menu e scegliere **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger. Pertanto, il primo passaggio consiste nel creare un progetto libreria di classi per la DLL.

## <a name="create-a-visualizer-manually"></a>Creare manualmente un visualizzatore

Eseguire le attività seguenti per creare un visualizzatore.

### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi

1. Nel menu **File** scegliere **Nuovo > Progetto**.

2. Nel **nuovo progetto** nella finestra di dialogo **Visual C#** , quindi selezionare **.NET Standard**.

3. Nel riquadro centrale, scegliere **libreria di classi**.

4. Nella casella **Nome** digitare un nome appropriato per la libreria di classi, ad esempio MyFirstVisualizer.

5. Fare clic su **OK**.

   Dopo avere creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter usare le classi definite in questa DLL. Prima di aggiungere il riferimento, tuttavia, è necessario rinominare alcune classi in modo che abbiano nomi significativi.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Per rinominare Class1.cs e aggiungere DebuggerVisualizers

1. Nelle **Esplora soluzioni**, fare doppio clic su Class1.cs e scegliere **rinominare** menu di scelta rapida.

2. Modificare il nome da Class1.cs in modo significativo, ad esempio DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dichiarazione di classe in base al nome del nuovo file DebuggerSide.cs modificata automaticamente.

3. Nelle **Esplora soluzioni**, fare doppio clic su **riferimenti** e scegliere **Aggiungi riferimento** menu di scelta rapida.

4. Nel **Aggiungi riferimento** finestra di dialogo il **.NET** scheda DebuggerVisualizers.

5. Fare clic su **OK**.

6. In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `using`:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   A questo punto è possibile creare il codice sul lato debugger. Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate. In primo luogo, è necessario modificare la dichiarazione del `DebuggerSide` in modo che eredita dalla classe di base dell'oggetto `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Per ereditare da DialogDebuggerVisualizer

1. In DebuggerSide.cs Vai alla riga di codice seguente:

   ```csharp
   public class DebuggerSide
   ```

2. Modificare il codice per:

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

  Il metodo `Show` contiene il codice per la creazione della finestra di dialogo del visualizzatore o un'altra interfaccia utente e per la visualizzazione delle informazioni passate al visualizzatore dal debugger. Questo codice deve essere aggiunto dallo sviluppatore. A tale scopo, in questa procedura dettagliata verrà usata una finestra di messaggio Windows Form. In primo luogo, è necessario aggiungere un riferimento e `using` informativa per System.

### <a name="to-add-systemwindowsforms"></a>Per aggiungere System.Windows.Forms

1. Nelle **Esplora soluzioni**, fare doppio clic su **riferimenti** e scegliere **Aggiungi riferimento** menu di scelta rapida.

2. Nel **Aggiungi riferimento** finestra di dialogo il **.NET** scheda, scegliere Forms.

3. Fare clic su **OK**.

4. In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `using`:

   ```csharp
   using System.Windows.Forms;
   ```

   A questo punto è necessario aggiungere una sezione di codice per la creazione e la visualizzazione dell'interfaccia utente del visualizzatore. Poiché si tratta del primo visualizzatore creato, verranno mantenere semplice l'interfaccia utente e usare una finestra di messaggio.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Per visualizzare l'output del visualizzatore in una finestra di dialogo

1. Nel metodo `Show` aggiungere la riga di codice seguente:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Questo codice di esempio non include la gestione degli errori. In un vero visualizzatore o in un qualsiasi altro tipo di applicazione è consigliabile includere la gestione degli errori.

2. Nel **compilare** menu, scegliere **compilare MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

   Il codice sul lato debugger è stato completato. È tuttavia necessario eseguire un altro passaggio, ovvero specificare l'attributo che indica al lato dell'oggetto del debug la raccolta di classi che comprende il visualizzatore.

### <a name="to-add-the-debuggee-side-code"></a>Per aggiungere il codice del lato oggetto del debug

1. Aggiungere il seguente codice di attributo per DebuggerSide.cs dopo il `using` istruzioni ma prima `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Nel **compilare** menu, scegliere **compilare MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

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

2. Nel **compilare** menu, scegliere **compilare MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.

   Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore. Per semplicità, si userà un progetto applicazione Console.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Per aggiungere un progetto applicazione console alla soluzione

1. Nel **File** menu, scegliere **Add** e quindi fare clic su **nuovo progetto**.

2. Nel **Aggiungi nuovo progetto** finestra di dialogo scegliere **Visual C#**   >  **Desktop di Windows**, quindi scegliere **applicazionediConsole**.

3. Nel **Name** , digitare un nome significativo per l'applicazione console, ad esempio `MyTestConsole`.

4. Fare clic su **OK**.

   A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Per aggiungere riferimenti necessari a MyTestConsole

1. Nelle **Esplora soluzioni**, fare doppio clic su **MyTestConsole** e scegliere **Aggiungi riferimento** menu di scelta rapida.

2. Nel **Aggiungi riferimento** della finestra di dialogo **.NET** scheda DebuggerVisualizers.

3. Fare clic su **OK**.

4. Fare doppio clic su **MyTestConsole** e scegliere **Aggiungi riferimento** nuovamente.

5. Nel **Aggiungi riferimento** della finestra di dialogo fare clic sui **progetti** scheda e quindi fare clic su MyFirstVisualizer.

6. Fare clic su **OK**.

   A questo punto verrà aggiunto il codice per completare il test harness.

### <a name="to-add-code-to-mytestconsole"></a>Per aggiungere codice a MyTestConsole

1. Nelle **Esplora soluzioni**, fare doppio clic su Program.cs e scegliere **rinominare** menu di scelta rapida.

2. Modificare il nome di Program.cs in modo più significativo, ad esempio TestConsole.cs.

    **Nota** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dichiarazione di classe in base al nome del nuovo file TestConsole.cs modificata automaticamente.

3. In base TestConsole.cs, aggiungere il codice seguente per il `using` istruzioni:

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

1. Nelle **Esplora soluzioni**, fare doppio clic su **MyTestConsole** e scegliere **imposta come progetto di avvio** menu di scelta rapida.

2. Scegliere **Avvia** dal menu **Debug**.

    Avvio dell'applicazione console e viene visualizzato il visualizzatore con la stringa "Hello, World".

   Il visualizzatore è stato compilato e sottoposto a test.

   Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo. Per altre informazioni, vedere [procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Creare un visualizzatore usando il modello di elemento

Finora, questa procedura dettagliata è stato illustrato come creare manualmente un visualizzatore. Questa operazione è stata eseguita come un esercizio di apprendimento. Dopo avere appreso come funziona un visualizzatore semplice, vi è un modo più semplice per crearne uno: usando il modello di elemento.

In primo luogo, è necessario creare un nuovo progetto di libreria di classi.

### <a name="to-create-a-new-class-library"></a>Per creare una nuova libreria di classi

1. Nel menu **File** scegliere **Nuovo > Progetto**.

2. Nel **nuovo progetto** nella finestra di dialogo **Visual C#** , selezionare **.NET Standard**.

3. Nel riquadro centrale, scegliere **libreria di classi**.

4. Nel **nome** , digitare un nome appropriato per la libreria di classi, ad esempio MySecondVisualizer.

5. Fare clic su **OK**.

   A questo punto, è possibile aggiungere un elemento del visualizzatore a esso:

### <a name="to-add-a-visualizer-item"></a>Per aggiungere un elemento del Visualizzatore

1. Nelle **Esplora soluzioni**, fare doppio clic su MySecondVisualizer.

2. Nel menu di scelta rapida, scegliere **Add** e quindi fare clic su **nuovo elemento**.

3. Nel **Aggiungi nuovo elemento** nella finestra di dialogo **Visual C# elementi**, selezionare **visualizzatore del Debugger**.

4. Nel **nome** , digitare un nome appropriato, ad esempio SecondVisualizer.cs.

5. Fare clic su **Aggiungi**.

   Che è tutto qui. Esaminare il file SecondVisualizer.cs e visualizzare il codice che il modello aggiunto automaticamente. Proseguo e provare a usare il codice. Dopo avere appreso le nozioni di base, è pronti per la creazione di visualizzatori personalizzati più complessi e utili.

## <a name="see-also"></a>Vedere anche

- [Architettura del visualizzatore](../debugger/visualizer-architecture.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)