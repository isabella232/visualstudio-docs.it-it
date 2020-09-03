---
title: 'Esercitazione 1: Creare un visualizzatore di immagini | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66988fa88ae347a2db08bf2f6d1b79ba3bcd80b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851328"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Esercitazione 1: creare un visualizzatore immagini
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa esercitazione si compila un programma che carica un'immagine da un file e la visualizza in una finestra. Viene illustrato come trascinare i controlli quali pulsanti e caselle immagine sul form, impostare le relative proprietà e utilizzare i contenitori per ridimensionare agevolmente il form. Si inizia inoltre a scrivere il codice. Si apprenderà come:

- Creare un nuovo progetto.

- Testare un'applicazione (eseguirne il debug).

- Aggiungere controlli di base come caselle di controllo e pulsanti a un form.

- Posizionare i controlli sul form utilizzando i layout.

- Aggiungere le finestre di dialogo **Apri file** e **Colore** a un form.

- Creare codice utilizzando IntelliSense e frammenti di codice.

- Scrivere metodi per la gestione eventi.

  Al termine delle varie procedure, il programma sarà simile all'immagine che segue.

  ![Immagine che si creerà in questa esercitazione](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone") Immagine che si creerà in questa esercitazione

  ![collegamento al video](../data-tools/media/playvideo.gif "PlayVideo") Per una versione video di questo argomento, vedere la procedura relativa alla [creazione di un visualizzatore di immagini in Visual Basic](https://msdn.microsoft.com/vstudio/gg315352) o [procedura: creare un visualizzatore immagini in C#](https://msdn.microsoft.com/vcsharp/gg278960.aspx).

> [!NOTE]
> In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio. In questa esercitazione sono trattati sia Visual C# sia Visual Basic; concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.
>
> Per visualizzare il codice per Visual Basic, scegliere la scheda **VB** nella parte superiore dei blocchi di codice. per visualizzare il codice per Visual C#, scegliere la scheda **C#** . Per ulteriori informazioni su Visual C++, vedere l'esercitazione [Introduzione](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) e il [linguaggio C++](http://www.cplusplus.com/doc/tutorial/).
>
> Per informazioni sulla scrittura di app Visual C# o Visual Basic per Windows Store, vedere [Creare la prima app di Windows Runtime in C# o Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Per informazioni sulla creazione di app JavaScript per Windows Store, vedere [Creazione della prima app di Windows Runtime in JavaScript](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Passaggio 1: creare un progetto di Windows Forms Application](../ide/step-1-create-a-windows-forms-application-project.md)|Iniziare creando un progetto di applicazione Windows Forms.|
|[Passaggio 2: eseguire il programma](../ide/step-2-run-your-program.md)|Eseguire il programma applicativo Windows Forms creato nel passaggio precedente.|
|[Passaggio 3: impostare le proprietà del form](../ide/step-3-set-your-form-properties.md)|Modificare l'aspetto del form usando la finestra **Proprietà**.|
|[Passaggio 4: creare il layout del form con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Aggiungere un oggetto `TableLayoutPanel` al form.|
|[Passaggio 5: aggiungere controlli al form](../ide/step-5-add-controls-to-your-form.md)|Aggiungere controlli, ad esempio un controllo `PictureBox` e un controllo `CheckBox`, al form. Aggiungere pulsanti al form.|
|[Passaggio 6: assegnare un nome ai controlli Button](../ide/step-6-name-your-button-controls.md)|Rinominare i pulsanti con nomi più significativi.|
|[Passaggio 7: aggiungere componenti della finestra di dialogo al form](../ide/step-7-add-dialog-components-to-your-form.md)|Aggiungere un componente **OpenFileDialog** e un componente **ColorDialog** al form.|
|[Passaggio 8: scrivere il codice per il gestore dell'evento del pulsante Visualizza immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Creare codice utilizzando lo strumento IntelliSense.|
|[Passaggio 9: esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md)|Esaminare e testare il codice. Aggiungere commenti in base alle necessità.|
|[Passaggio 10: scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Scrivere codice per far funzionare altri pulsanti e una casella di controllo utilizzando IntelliSense.|
|[Passaggio 11: eseguire il programma e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md)|Eseguire il programma e impostare il colore di sfondo. Provare altre funzionalità, ad esempio la modifica di colori, tipi di carattere e bordi.|
