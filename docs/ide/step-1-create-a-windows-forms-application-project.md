---
title: 'Passaggio 1: Creare un progetto di Windows Forms Application'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86942dda1990fe8a681ec2832b2474d42d418a63
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842057"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Passaggio 1: Creare un progetto di Windows Forms Application
Quando si crea un visualizzatore di immagini, il primo passaggio consiste nella creazione di un progetto di Windows Forms Application.

 ![Collegamento a video](../data-tools/media/playvideo.gif)Per una versione video di questo argomento, vedere [Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic - Video 1](http://go.microsoft.com/fwlink/?LinkId=205209) o [Esercitazione 1: Creare un visualizzatore immagini in C# - Video 1](http://go.microsoft.com/fwlink/?LinkId=205199). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.

## <a name="to-create-a-windows-forms-application-project"></a>Per creare un progetto di Windows Forms Application

1.  Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**. Verrà visualizzata una finestra di dialogo simile alla seguente.

     ![Finestra di dialogo Nuovo progetto](../ide/media/newprojectdialogcallouts.png)
Finestra di dialogo **Nuovo progetto**

2.  Scegliere **Visual C#** o **Visual Basic** dall'elenco **Modelli installati**.

3.  Nell'elenco di modelli scegliere l'icona **Windows Forms Application**. Assegnare il nome **PictureViewer** al nuovo form, quindi scegliere il pulsante **OK**.

     Visual Studio crea una soluzione per il programma. Una soluzione funge da contenitore per tutti i progetti e i file richiesti dal programma. Questi termini verranno spiegati dettagliatamente più avanti in questa esercitazione.

4.  Nella figura seguente viene illustrato ciò che si dovrebbe vedere nell'interfaccia di Visual Studio.

    > [!NOTE]
    >  Il layout delle finestre potrebbe non essere esattamente uguale a questa illustrazione. Il layout preciso della finestra dipende dalla versione di Visual Studio, dal linguaggio di programmazione in uso e da altri fattori. Tuttavia, è necessario verificare che tutte e tre le finestre siano visualizzate.

     ![Finestra IDE](../ide/media/express_ideoverview_visio.png)
Finestra **IDE**

     L'interfaccia contiene tre finestre: una finestra principale, **Esplora soluzioni** e **Proprietà**.

     Se manca una di queste finestre, ripristinare il layout di finestra predefinito, scegliendo **Finestra** > **Reimposta layout finestra** sulla barra dei menu. È inoltre possibile visualizzare le finestre tramite i comandi di menu. Sulla barra dei menu scegliere **Visualizza** > **Finestra Proprietà** o **Esplora soluzioni**. Se sono aperte altre finestre, chiuderle scegliendo il pulsante **Chiudi** (x) negli angoli in alto a destra.

5.  Nella figura sono illustrate le finestre seguenti (in senso orario dall'angolo superiore sinistro):

    -   **Finestra principale** In questa finestra viene eseguita la maggior parte del lavoro, come l'utilizzo dei form e la modifica del codice. La finestra nella figura contiene un modulo nell'**editor di moduli**. Nella parte superiore della finestra vengono visualizzate la scheda **Pagina iniziale** e la scheda **Form1.cs [Progettazione]**. In Visual Basic il nome della scheda termina con l'estensione *VB* invece di *CS*.

    -   **Finestra Esplora soluzioni** In questa finestra è possibile visualizzare tutti gli elementi della soluzione e spostarsi tra di essi. Se si sceglie un file, cambia il contenuto della finestra **Proprietà**. Se si apre un file di codice (che termina con l'estensione *CS* in Visual C# e *VB* in Visual Basic), viene visualizzato il file stesso o la relativa finestra di progettazione. Una finestra di progettazione è una superficie visiva in cui è possibile aggiungere controlli quali pulsanti ed elenchi. Per i moduli di Visual Studio, la finestra di progettazione è denominata **Progettazione Windows Form**.

    -   **Finestra Proprietà** In questa finestra è possibile modificare le proprietà degli elementi scelti nelle altre finestre. Ad esempio, se si sceglie Form1, è possibile modificarne il titolo impostando la proprietà **Text** e il colore di sfondo impostando la proprietà **Backcolor**.

    > [!NOTE]
    >  Nella riga superiore in **Esplora soluzioni** è riportata la dicitura **Soluzione "PictureViewer" (1 progetto)** per indicare che è stata creata una soluzione in Visual Studio. Una soluzione può contenere più progetti, ma per ora verranno utilizzate soluzioni che contengono un solo progetto.

6.  Sulla barra dei menu scegliere **File** > **Salva tutto**.

     In alternativa, scegliere il pulsante **Salva tutto** sulla barra degli strumenti, come illustrato nella figura seguente.

     ![Pulsante della barra degli strumenti Salva tutto](../ide/media/express_iconsaveall.png)
Pulsante della barra degli strumenti **Salva tutto**

     In Visual Studio il nome della cartella e il nome del progetto vengono compilati automaticamente. Il progetto viene quindi salvato nella cartella dei progetti.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

-   Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 2: Eseguire il programma](../ide/step-2-run-your-program.md).

-   Per tornare all'argomento introduttivo, vedere [Esercitazione 1: Creare un visualizzatore di immagini](../ide/tutorial-1-create-a-picture-viewer.md).
