---
title: 'Procedura dettagliata: Scrittura di un visualizzatore in Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eba9efa9710a3dd439b1cd47e4df777a76d781aa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444241"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Procedura dettagliata: Scrittura di un visualizzatore in Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene descritto come utilizzare [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] per scrivere un visualizzatore semplice che consente di visualizzare il contenuto di una stringa in una finestra di messaggio di Windows Form. Questo visualizzatore semplice di stringhe è un esempio base per illustrare la creazione di visualizzatori per altri tipi di dati più applicabili ai progetti.  
  
> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, passare al menu **Strumenti** e scegliere **Importa/Esporta**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il codice del visualizzatore deve essere inserito in una DLL, che verrà letta dal debugger. La prima operazione da effettuare consiste nel creare un progetto Libreria di classi per la DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Creare e preparare un progetto Libreria di classi  
  
#### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi  
  
1. Nel menu **File** scegliere **Nuovo** e fare clic su **Nuovo progetto**.  
  
2. Nel **nuovo progetto** nella finestra di dialogo **tipo di progetto**s, fare clic su **Visual Basic**.  
  
3. Nel **modelli** fare clic su **libreria di classi**.  
  
4. Nella casella **Nome** digitare un nome appropriato per la libreria di classi, ad esempio **MyFirstVisualizer**.  
  
5. Fare clic su **OK**.  
  
   Dopo avere creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter utilizzare le classi definite in questa DLL. Innanzitutto è opportuno assegnare al progetto un nome significativo.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Per rinominare Class1.vb e aggiungere Microsoft.VisualStudio.DebuggerVisualizers  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Class1.vb** e scegliere **Rinomina** dal menu di scelta rapida.  
  
2. Sostituire Class1.vb con un nome significativo, ad esempio DebuggerSide.vb.  
  
    > [!NOTE]
    > In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la dichiarazione di classe viene modificata automaticamente in base al nuovo nome di file DebuggerSide.vb.  
  
3. In **Esplora soluzioni** fare clic son il pulsante destro del mouse su **My First Visualizer** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
4. Nella finestra di dialogo **Aggiungi riferimento** nella scheda **.NET** fare clic su Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5. Fare clic su **OK**.  
  
6. In DebuggerSide.vb aggiungere l'istruzione seguente alle istruzioni `Imports`:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Aggiungere il codice sul lato debugger  
 A questo punto è possibile creare il codice sul lato debugger. Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate. È innanzitutto necessario modificare la dichiarazione dell'oggetto `DebuggerSide` in modo da ereditare dalla classe di base `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Per ereditare da DialogDebuggerVisualizer  
  
1. In DebuggerSide.vb posizionarsi sulla riga di codice seguente:  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Modificare il codice nel modo seguente:  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` dispone di un metodo astratto, `Show`, di cui è necessario eseguire l'override.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Per eseguire l'override del metodo DialogDebuggerVisualizer.Show  
  
- In `public class DebuggerSide` aggiungere il metodo seguente:  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  Il metodo `Show` contiene il codice per la creazione della finestra di dialogo del visualizzatore o un'altra interfaccia utente e per la visualizzazione delle informazioni passate al visualizzatore dal debugger. Questo codice deve essere aggiunto dallo sviluppatore. A tale scopo, in questa procedura dettagliata verrà utilizzata una finestra di messaggio Windows Form. È innanzitutto necessario aggiungere un riferimento e l'istruzione `Imports` per <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Per aggiungere System.Windows.Forms  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Riferimenti** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
2. Nella finestra di dialogo **Aggiungi riferimento** nella scheda **.NET** fare clic su **System.Windows.Forms**.  
  
3. Fare clic su **OK**.  
  
4. In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `Imports`:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Creare un'interfaccia utente del visualizzatore  
 A questo punto è necessario aggiungere una sezione di codice per la creazione e la visualizzazione dell'interfaccia utente del visualizzatore. Poiché si tratta del primo visualizzatore creato, l'interfaccia utente sarà semplice e verrà utilizzata una finestra di messaggio.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Per visualizzare l'output del visualizzatore in una finestra di dialogo  
  
1. Nel metodo `Show` aggiungere la riga di codice seguente:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Questo codice di esempio non include la gestione degli errori. In un vero visualizzatore o in un qualsiasi altro tipo di applicazione è consigliabile includere la gestione degli errori.  
  
2. Scegliere **Compila MyFirstVisualizer** dal menu **Compila**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
## <a name="add-the-necessary-attribute"></a>Aggiungere l'attributo necessario  
 Il codice sul lato debugger è stato completato. È tuttavia necessario eseguire un altro passaggio, ovvero specificare l'attributo che indica al lato dell'oggetto del debug la raccolta di classi che comprende il visualizzatore.  
  
#### <a name="to-add-the-debugee-side-code"></a>Per aggiungere il codice del lato oggetto del debug  
  
1. Aggiungere il codice di attributo seguente a DebuggerSide.vb, dopo le istruzioni `Imports` ma prima di `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2. Scegliere **Compila MyFirstVisualizer** dal menu **Compila**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
## <a name="create-a-test-harness"></a>Creare un test harness  
 A questo punto il visualizzatore è pronto. Se la procedura è stata completata in modo corretto, è possibile compilare il visualizzatore e installarlo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Prima di installare un visualizzatore in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è tuttavia consigliabile testarlo per assicurarsi che funzioni in modo corretto. Di seguito viene descritto come creare un test harness per eseguire il visualizzatore senza installarlo in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Per aggiungere un metodo di test per visualizzare il visualizzatore  
  
1. Aggiungere il metodo seguente alla classe `public DebuggerSide`:  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. Scegliere **Compila MyFirstVisualizer** dal menu **Compila**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
   Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore. Per semplicità, utilizzare un progetto applicazione console.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Per aggiungere un progetto applicazione console alla soluzione  
  
1. Nel menu **File** fare clic su **Aggiungi** e quindi fare clic su **Nuovo progetto**.  
  
2. Nel **Aggiungi nuovo progetto** nella finestra di dialogo il **modelli** fare clic su **applicazione Console**.  
  
3. Nella casella **Nome** digitare un nome significativo per l'applicazione console, ad esempio **MyTestConsole**.  
  
4. Fare clic su **OK**.  
  
   A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Per aggiungere riferimenti necessari a MyTestConsole  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyTestConsole**, quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
2. Nella finestra di dialogo **Aggiungi riferimento** nella scheda **.NET** fare clic su Microsoft.VisualStudio.DebuggerVisualizers.  
  
3. Fare clic su **OK**.  
  
4. Fare clic con il pulsante destro del mouse su **MyTestConsole** e scegliere nuovamente **Aggiungi riferimento**.  
  
5. Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Progetti** e selezionare MyFirstVisualizer.  
  
6. Fare clic su **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Completare il test harness ed eseguire il test del visualizzatore  
 A questo punto verrà aggiunto il codice per completare il test harness.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Per aggiungere codice a MyTestConsole  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Program.vb** e scegliere **Rinomina** dal menu di scelta rapida.  
  
2. Sostituire Module1.vb con un nome appropriato, ad esempio **TestConsole.vb**.  
  
    Si noti che in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la dichiarazione di classe viene modificata automaticamente in TestConsole.vb in base al nuovo nome file.  
  
3. In TestConsole. vb, aggiungere il codice seguente `Imports` istruzione:  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. Nel metodo `Main` aggiungere il codice seguente:  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   A questo punto è possibile eseguire il test del visualizzatore.  
  
#### <a name="to-test-the-visualizer"></a>Per eseguire il test del visualizzatore  
  
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **MyTestConsole** e scegliere **Imposta come progetto di avvio** dal menu di scelta rapida.  
  
2. Nel menu **Debug** fare clic su **Avvia**.  
  
    Verrà avviata l'applicazione console. Verrà aperto il visualizzatore contenente la stringa "Hello, World".  
  
   Il visualizzatore è stato compilato e sottoposto a test.  
  
   Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo. Per altre informazioni, vedere [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura del visualizzatore](../debugger/visualizer-architecture.md)   
 [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
