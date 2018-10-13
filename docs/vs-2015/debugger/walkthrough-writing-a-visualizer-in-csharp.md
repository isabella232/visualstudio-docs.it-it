---
title: 'Procedura dettagliata: Scrittura di un visualizzatore in c# | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd8c12e415b37f04635327d195ef0f96649a2894
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199186"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procedura dettagliata: scrittura di un visualizzatore in C# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come scrivere un visualizzatore semplice usando c#. Il visualizzatore che verrà creato in questa procedura dettagliata consente di visualizzare il contenuto di una stringa usando una finestra di messaggio Windows Form. Questo visualizzatore semplice di stringhe non è particolarmente utile di per sé, ma mostra i passaggi di base che è necessario seguire per creare più utili visualizzatori per altri tipi di dati.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, vedere il **strumenti** menu e scegliere **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger. Pertanto, il primo passaggio consiste nel creare un progetto libreria di classi per la DLL.  
  
#### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi  
  
1.  Nel **File** menu, scegliere **New** e quindi fare clic su **nuovo progetto**.  
  
2.  Nel **nuovo progetto** nella finestra di dialogo **tipo di progetto**s, selezionare **Visual c#**.  
  
3.  Nel **modelli** , scegliere **libreria di classi**.  
  
4.  Nel **nome** , digitare un nome appropriato per la libreria di classi, ad esempio MyFirstVisualizer.  
  
5.  Fare clic su **OK**.  
  
 Dopo aver creato la libreria di classi, è necessario aggiungere un riferimento a DebuggerVisualizers in modo che è possibile usare le classi definite non esiste. Prima di aggiungere il riferimento, tuttavia, è necessario rinominare alcune classi in modo che abbiano nomi significativi.  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Per rinominare Class1.cs e aggiungere DebuggerVisualizers  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su Class1.cs e scegliere **rinominare** menu di scelta rapida.  
  
2.  Modificare il nome da Class1.cs in modo significativo, ad esempio DebuggerSide.cs.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la dichiarazione di classe in base al nome del nuovo file DebuggerSide.cs modificata automaticamente.  
  
3.  Nelle **Esplora soluzioni**, fare doppio clic su **riferimenti** e scegliere **Aggiungi riferimento** menu di scelta rapida.  
  
4.  Nel **Aggiungi riferimento** finestra di dialogo il **.NET** scheda DebuggerVisualizers.  
  
5.  Fare clic su **OK**.  
  
6.  In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `using`:  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 A questo punto si è pronti per creare il codice del lato debugger. Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate. In primo luogo, è necessario modificare la dichiarazione del `DebuggerSide` in modo che eredita dalla classe di base dell'oggetto `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Per ereditare da DialogDebuggerVisualizer  
  
1.  In DebuggerSide.cs Vai alla riga di codice seguente:  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  Modificare il codice per:  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` dispone di un metodo astratto (`Show`) che è necessario eseguire l'override.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Per eseguire l'override del metodo DialogDebuggerVisualizer.Show  
  
-   Nelle `public class DebuggerSide`, aggiungere il codice seguente **metodo:**  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 Il `Show` metodo contiene il codice che effettivamente crea la finestra di dialogo Visualizzatore o un'altra interfaccia utente e visualizza le informazioni che sono state passate al visualizzatore dal debugger. Questo codice deve essere aggiunto dallo sviluppatore. In questa procedura dettagliata, si eseguirà questo usando una finestra di messaggio Windows Form. In primo luogo, è necessario aggiungere un riferimento e `using` informativa per System.  
  
#### <a name="to-add-systemwindowsforms"></a>Per aggiungere System.Windows.Forms  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su **riferimenti** e scegliere **Aggiungi riferimento** menu di scelta rapida.  
  
2.  Nel **Aggiungi riferimento** finestra di dialogo il **.NET** scheda, scegliere Forms.  
  
3.  Fare clic su **OK**.  
  
4.  In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `using`:  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 A questo punto, si aggiungerà codice per creare e visualizzare l'interfaccia utente del visualizzatore. Poiché si tratta del primo visualizzatore creato, verranno mantenere semplice l'interfaccia utente e usare una finestra di messaggio.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Per visualizzare l'Output del visualizzatore in una finestra di dialogo  
  
1.  Nel metodo `Show` aggiungere la riga di codice seguente:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Questo codice di esempio non include la gestione degli errori. È necessario includere in un vero visualizzatore o qualsiasi altro tipo di applicazione di gestione degli errori.  
  
2.  Nel **compilare** menu, scegliere **compilare MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
 Che rappresenta la fine del codice sul lato debugger. C'è un altro passaggio, tuttavia; l'attributo che indica il lato oggetto del debug la raccolta di classi che comprende il visualizzatore.  
  
#### <a name="to-add-the-debuggee-side-code"></a>Per aggiungere il codice del lato oggetto del debug  
  
1.  Aggiungere il seguente codice di attributo per DebuggerSide.cs dopo il `using` istruzioni ma prima `namespace MyFirstVisualizer`:  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  Nel **compilare** menu, scegliere **compilare MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
 A questo punto il visualizzatore è pronto. Se la procedura è stata completata in modo corretto, è possibile compilare il visualizzatore e installarlo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Prima di installare un visualizzatore in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è tuttavia consigliabile testarlo per assicurarsi che funzioni in modo corretto. Di seguito viene descritto come creare un test harness per eseguire il visualizzatore senza installarlo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Per aggiungere un metodo di Test per visualizzare il Visualizzatore  
  
1.  Aggiungere il metodo seguente alla classe `public DebuggerSide`:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  Nel **compilare** menu, scegliere **compilare MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
 Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore. Per semplicità, si userà un progetto applicazione Console.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Per aggiungere un progetto applicazione console alla soluzione  
  
1.  Nel **File** menu, scegliere **Add** e quindi fare clic su **nuovo progetto**.  
  
2.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo il **modelli** , seleziona **applicazione Console**.  
  
3.  Nel **Name** , digitare un nome significativo per l'applicazione console, ad esempio `MyTestConsole`.  
  
4.  Fare clic su **OK**.  
  
 A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Per aggiungere riferimenti necessari a MyTestConsole  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su **MyTestConsole** e scegliere **Aggiungi riferimento** menu di scelta rapida.  
  
2.  Nel **Aggiungi riferimento** della finestra di dialogo **.NET** scheda DebuggerVisualizers.  
  
3.  Fare clic su **OK**.  
  
4.  Fare doppio clic su **MyTestConsole** e scegliere **Aggiungi riferimento** nuovamente.  
  
5.  Nel **Aggiungi riferimento** della finestra di dialogo fare clic sui **progetti** scheda e quindi fare clic su MyFirstVisualizer.  
  
6.  Fare clic su **OK**.  
  
 A questo punto verrà aggiunto il codice per completare il test harness.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Per aggiungere codice a MyTestConsole  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su Program.cs e scegliere **rinominare** menu di scelta rapida.  
  
2.  Modificare il nome di Program.cs in modo più significativo, ad esempio TestConsole.cs.  
  
     **Nota** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la dichiarazione di classe in base al nome del nuovo file TestConsole.cs modificata automaticamente.  
  
3.  In base TestConsole.cs, aggiungere il codice seguente per il `using` istruzioni:  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  Nel metodo `Main` aggiungere il codice seguente:  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 A questo punto, si è pronti per eseguire il test del visualizzatore.  
  
#### <a name="to-test-the-visualizer"></a>Per eseguire il test del visualizzatore  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su **MyTestConsole** e scegliere **imposta come progetto di avvio** menu di scelta rapida.  
  
2.  Nel **Debug** menu, scegliere **avviare**.  
  
     Avvio dell'applicazione console e viene visualizzato il visualizzatore con la stringa "Hello, World".  
  
 Il visualizzatore è stato compilato e sottoposto a test.  
  
 Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo. Per altre informazioni, vedere [procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="using-the-visualizer-item-template"></a>Usando il modello di elemento  
 Finora, questa procedura dettagliata è stato illustrato come creare manualmente un visualizzatore. Questa operazione è stata eseguita come un esercizio di apprendimento. Dopo avere appreso come funziona un visualizzatore semplice, vi è un modo più semplice per crearne uno: usando il modello di elemento.  
  
 In primo luogo, è necessario creare un nuovo progetto di libreria di classi.  
  
#### <a name="to-create-a-new-class-library"></a>Per creare una nuova libreria di classi  
  
1.  Nel **File** menu, scegliere **Add** e quindi fare clic su **nuovo progetto**.  
  
2.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo **tipo di progetto**s, selezionare **Visual c#**.  
  
3.  Nel **modelli** , scegliere **libreria di classi**.  
  
4.  Nel **nome** , digitare un nome appropriato per la libreria di classi, ad esempio MySecondVisualizer.  
  
5.  Fare clic su **OK**.  
  
 A questo punto, è possibile aggiungere un elemento del visualizzatore a esso:  
  
#### <a name="to-add-a-visualizer-item"></a>Per aggiungere un elemento del Visualizzatore  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su MySecondVisualizer.  
  
2.  Nel menu di scelta rapida, scegliere **Add** e quindi fare clic su **nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **modelli**, **Modelli Visual Studio installati**, selezionare **visualizzatore del Debugger**.  
  
4.  Nel **nome** , digitare un nome appropriato, ad esempio SecondVisualizer.cs.  
  
5.  Fare clic su **Aggiungi**.  
  
 Che è tutto qui. Esaminare il file SecondVisualizer.cs e visualizzare il codice che il modello aggiunto automaticamente. Proseguo e provare a usare il codice. Dopo avere appreso le nozioni di base, è pronti per la creazione di visualizzatori personalizzati più complessi e utili.  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura del Visualizzatore](../debugger/visualizer-architecture.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)



