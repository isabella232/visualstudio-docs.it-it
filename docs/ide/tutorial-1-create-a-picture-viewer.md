---
title: 'Esercitazione 1: Creare un visualizzatore di immagini'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b26b70b4887b792bd7a0a16bc3291d4e8fae369
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2018
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Esercitazione 1: Creare un visualizzatore di immagini
In questa esercitazione si compila un programma che carica un'immagine da un file e la visualizza in una finestra. Viene illustrato come trascinare i controlli quali pulsanti e caselle immagine sul modulo, impostare le relative proprietà e utilizzare i contenitori per ridimensionare agevolmente il modulo. Si inizia inoltre a scrivere il codice. Vengono illustrate le seguenti procedure:  

-   Creare un nuovo progetto.  

-   Testare un'applicazione (eseguirne il debug).  

-   Aggiungere controlli di base come caselle di controllo e pulsanti a un modulo.  

-   Posizionare i controlli sul modulo utilizzando i layout.  

-   Aggiungere le finestre di dialogo **Apri file** e **Colore** a un modulo.  

-   Creare codice utilizzando IntelliSense e frammenti di codice.  

-   Scrivere metodi per la gestione eventi.  

 Al termine delle varie procedure, il programma sarà simile all'immagine che segue.  

 ![Immagine creata in questa esercitazione](../ide/media/express_pictureviewerdone.png "Express_PictureViewerDone")  
Immagine che si creerà in questa esercitazione  

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

 Per scaricare una versione completa dell'esempio, vedere [Complete Picture Viewer tutorial sample](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Esercitazione di esempio completa per un visualizzatore di immagini).  

 ![collegamento al video](../data-tools/media/playvideo.gif "Riproduci video")Per una versione video di questo argomento, vedere [How Do I: Create a Picture Viewer in Visual Basic?](http://go.microsoft.com/fwlink/?LinkId=205207) (Come creare un visualizzatore di immagini in Visual Basic) o [How Do I: Create a Picture Viewer in C#?](http://go.microsoft.com/fwlink/?LinkId=205198) (Come creare un visualizzatore di immagini in C#).  

> [!NOTE]
>  In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio. In questa esercitazione sono trattati sia Visual C# sia Visual Basic; concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.  
>   
>  Per visualizzare il codice per Visual Basic, scegliere la scheda **VB** all'inizio dei blocchi di codice; per visualizzare il codice per Visual C#, scegliere la scheda **C#**. Per altre informazioni su Visual C++, vedere l'[introduzione](../ide/getting-started-with-cpp-in-visual-studio.md) e l'[esercitazione sul linguaggio C++](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Se si è interessati a imparare a scrivere App Visual C# o una piattaforma UWP Visual Basic, vedere [Sviluppare app UWP](https://developer.microsoft.com/windows/apps).

## <a name="related-topics"></a>Argomenti correlati  

|Titolo|Descrizione|  
|-----------|-----------------|  
|[Passaggio 1: Creare un progetto di applicazione Windows Form](../ide/step-1-create-a-windows-forms-application-project.md)|Iniziare creando un progetto di applicazione Windows Form.|  
|[Passaggio 2: Eseguire il programma](../ide/step-2-run-your-program.md)|Eseguire il programma applicativo Windows Form creato nel passaggio precedente.|  
|[Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md)|Modificare l'aspetto del modulo usando la finestra **Proprietà**.|  
|[Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Aggiungere un oggetto `TableLayoutPanel` al modulo.|  
|[Passaggio 5: Aggiungere controlli al modulo](../ide/step-5-add-controls-to-your-form.md)|Aggiungere controlli, ad esempio un controllo `PictureBox` e un controllo `CheckBox`, al modulo. Aggiungere pulsanti al modulo.|  
|[Passaggio 6: Assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md)|Rinominare i pulsanti con nomi più significativi.|  
|[Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo](../ide/step-7-add-dialog-components-to-your-form.md)|Aggiungere un componente `OpenFileDialog` e un componente `ColorDialog` al modulo.|  
|[Passaggio 8: Scrivere codice per il gestore dell'evento del pulsante Mostra immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Creare codice utilizzando lo strumento IntelliSense.|  
|[Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md)|Esaminare e testare il codice. Aggiungere commenti in base alle necessità.|  
|[Passaggio 10: Scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Scrivere codice per far funzionare altri pulsanti e una casella di controllo utilizzando IntelliSense.|  
|[Passaggio 11: Eseguire il programma e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md)|Eseguire il programma e impostare il colore di sfondo. Provare altre funzionalità, ad esempio la modifica di colori, tipi di carattere e bordi.|
