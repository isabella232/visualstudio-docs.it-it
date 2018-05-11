---
title: 'Passaggio 6: Assegnare un nome ai pulsanti'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57fec877b968873cb4571fe060572ffb2e6aeba3
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2018
---
# <a name="step-6-name-your-button-controls"></a>Passaggio 6: Assegnare un nome ai pulsanti
Nel modulo c'è un solo oggetto <xref:System.Windows.Forms.PictureBox>. Quando è stato aggiunto, l'IDE lo ha automaticamente denominato **pictureBox1**. C'è un solo oggetto <xref:System.Windows.Forms.CheckBox>, denominato **checkBox1**. Presto si scriverà del codice che farà riferimento ai controlli CheckBox e PictureBox. Poiché è presente uno solo di ognuno di questi controlli, sarà possibile riconoscerlo quando si vedrà **pictureBox1** o **checkBox1** nel codice.  

> [!NOTE]
>  In Visual Basic, l'impostazione predefinita per la prima lettera di qualsiasi nome di controllo è la maiuscola, pertanto i nomi sono **PictureBox1**, **CheckBox1**e così via.  

 Vi sono quattro pulsanti nel modulo e l'IDE li ha denominati **button1**, **button2**, **button3**e **button4**. Da un semplice sguardo ai nomi correnti non è possibile capire quale pulsante corrisponda al pulsante **Chiudi** e quale corrisponda al pulsante **Mostra immagine** . È questo il motivo per cui è utile assegnare nomi più descrittivi ai pulsanti.  
  
 ![collegamento al video](../data-tools/media/playvideo.gif "Riproduci video")Per una versione video di questo argomento, vedere [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) (Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic - Video 3) o [Tutorial 1: Create a Picture Viewer in C# - Video 3](http://go.microsoft.com/fwlink/?LinkId=205202) (Esercitazione 1: Creare un visualizzatore di immagini in C# - Video 3). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.  
  
## <a name="to-name-your-button-controls"></a>Per assegnare un nome ai pulsanti  
  
1.  Nel modulo scegliere il pulsante **Chiudi** . Se sono ancora selezionati tutti i pulsanti, premere **ESC** per annullare la selezione. Scorrere nella finestra **Proprietà** fino a quando non viene visualizzata la proprietà **(Name)**. La proprietà **(Name)** è disponibile nella parte iniziale quando le proprietà sono ordinate alfabeticamente. Impostare il nome su **closeButton**, come mostrato nell'immagine seguente.  
  
     ![Finestra Proprietà con il nome closeButton](../ide/media/express_setnameproperty.png "Express_SetNameProperty")  
Finestra **Proprietà** con nome **closeButton**  
  
    > [!NOTE]
    >  Se si tenta di modificare il nome del pulsante in **closeButton**, con uno spazio tra le parole close e Button, l'IDE visualizza un messaggio di errore: "Valore di proprietà non valido". Gli spazi (e alcuni altri caratteri) non sono consentiti nei nomi dei controlli.  

2.  Rinominare gli altri tre pulsanti **backgroundButton**, **clearButton**e **showButton**. È possibile verificare i nomi facendo clic sull'elenco a discesa del selettore dei controlli nella finestra **Proprietà** . Vengono visualizzati i nuovi nomi dei pulsanti.  
  
3.  Fare doppio clic sul pulsante **Mostra immagine** nel modulo. In alternativa, scegliere il pulsante **Mostra immagine** nel modulo e quindi premere **INVIO**. Quando si esegue questa operazione, nell''IDE viene aperta una scheda aggiuntiva nella finestra principale denominata **Form1.cs** (**Form1.vb** se si usa Visual Basic). In questa scheda è riportato il file di codice sottostante del modulo, come illustrato nell'immagine seguente.  
  
     ![Scheda Form1.cs con codice Visual C&#35;](../ide/media/express_showbuttoncode.png "Express_ShowButtonCode")  
Scheda **Form1.cs** con codice Visual C#  
  
4.  Concentrare l'attenzione su questa parte del codice. Se si usa Visual Basic, scegliere la scheda **VB** nell'area sottostante per visualizzare la versione Visual Basic del codice.  

     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]  

     Si tratta del codice denominato `showButton_Click()` È stato aggiunto dall'IDE nel codice del modulo quando si è aperto il file di codice per il pulsante **showButton** . In fase di progettazione, quando si apre il file di codice per un controllo in un modulo, il codice, se non esiste già, viene generato per il controllo. Questo codice, noto come *metodo*, viene eseguito quando si esegue il programma e si sceglie il controllo, in questo caso il pulsante **Mostra immagine** .  

    > [!NOTE]
    >  In questa esercitazione, il codice Visual Basic che viene generato automaticamente è stato semplificato rimuovendo tutto il contenuto tra parentesi, `()`. Ogniqualvolta si verifica ciò, è possibile rimuovere lo stesso codice. Il programma funzionerà in entrambi i casi. Per il resto delle esercitazioni, eventuale codice generato automaticamente verrà semplificato, se possibile.  
  
5.  Scegliere ancora la scheda **Progettazione Windows Form** (**Form1.cs [Design]** in Visual C#, **Form1.vb [Design]** in Visual Basic) e quindi aprire il file di codice per il pulsante **Cancella immagine** per creare un metodo per il pulsante nel codice del modulo. Ripetere questa operazione per i restanti due pulsanti. L'IDE aggiunge ogni volta un nuovo metodo al file del codice del modulo.  
  
6.  Per aggiungere un altro metodo, aprire il file di codice per il controllo **CheckBox** in **Progettazione Windows Form**, in modo che l'IDE aggiunga un metodo `checkBox1_CheckedChanged()`. Tale metodo viene chiamato ogni volta che l'utente seleziona o deseleziona la casella di controllo.  
  
    > [!NOTE]
    >  Quando si crea un programma, si passa spesso dall'editor di codice a **Progettazione Windows Form** e viceversa. L'IDE facilita lo spostamento nel progetto. Usare **Esplora soluzioni** per aprire **Progettazione Windows Form** facendo doppio clic su *Form1.cs* in Visual C# o *Form1.vb* in Visual Basic oppure scegliere **Visualizza** > **Finestra di progettazione** sulla barra dei menu.  
  
     Di seguito viene mostrato il nuovo codice visualizzato nell'editor di codice.  

     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]  

     I cinque metodi aggiunti sono denominati *gestori di eventi*, perché vengono chiamati dal programma ogni volta che si verifica un evento, ad esempio, quando un utente sceglie un pulsante o seleziona una casella.  
  
     Quando si visualizza il codice per un controllo nell'IDE in fase di progettazione, in Visual Studio viene aggiunto un metodo del gestore eventi per il controllo, se non è presente. Ad esempio, quando si fa doppio clic su un pulsante, l'IDE aggiunge un gestore dell'evento per il relativo evento <xref:System.Windows.Forms.Control.Click>, che viene chiamato ogni volta che l'utente fa clic sul pulsante. Quando si fa doppio clic su una casella di controllo, l'IDE aggiunge un gestore dell'evento per il relativo evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>, che viene chiamato ogni volta che l'utente seleziona o deseleziona la casella.  
  
     Dopo aver aggiunto un gestore dell'evento per un controllo, è possibile tornarvi in qualsiasi momento da **Progettazione Windows Form** facendo doppio clic sul controllo o scegliendo **Visualizza** > **Codice** sulla barra dei menu.  
  
     I nomi sono importanti quando si compilano programmi e i metodi (inclusi i gestori di eventi) possono avere qualsiasi nome si desideri. Quando si aggiunge un gestore dell'evento con l'IDE, viene creato un nome basato sul nome del controllo e sull'evento gestito. Ad esempio, l'evento Click per un pulsante denominato **showButton** viene chiamato metodo del gestore dell'evento `showButton_Click()` . Inoltre, vengono generalmente aggiunte parentesi di apertura e chiusura `()` dopo il nome del metodo, per indicare che si tratta di metodi. Se si decide di modificare il nome di una variabile di codice, fare clic con il pulsante destro del mouse sulla variabile nel codice e quindi scegliere **Refactoring** > **Rinomina**. Tutte le istanze della variabile nel codice vengono rinominate. Vedere [Refactoring di ridenominazione](../ide/reference/rename.md) per altre informazioni.
  
## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo](../ide/step-7-add-dialog-components-to-your-form.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: Aggiungere controlli al modulo](../ide/step-5-add-controls-to-your-form.md).
