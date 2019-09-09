---
title: 'Esercitazione 1: Creare un visualizzatore di immagini'
ms.date: 08/30/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1506f4303cf5344c4035642cfdd3e42c98396b02
ms.sourcegitcommit: bd4e45f1697a8fbfdbc0a7c6b531c8f7b9fb8a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808781"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Esercitazione 1: Creare un visualizzatore di immagini

In questa esercitazione viene compilata un'app che carica un'immagine da un file e la Visualizza in una finestra. Si apprenderà come usare il **Progettazione Windows Form** per trascinare controlli quali pulsanti e caselle immagine nel form, impostarne le proprietà e usare i contenitori per ridimensionare il form in modo uniforme. Si inizia inoltre a scrivere il codice.

> [!NOTE]
> In questa esercitazione sono trattati sia Visual C# sia Visual Basic; concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.

Questa esercitazione illustra le attività seguenti:

* Creare un nuovo progetto.

* Testare un'applicazione (eseguirne il debug).

* Aggiungere controlli di base come caselle di controllo e pulsanti a un form.

* Posizionare i controlli in un form utilizzando i layout.

* Aggiungere le finestre di dialogo **Apri file** e **Colore** a un form.

* Scrivere codice usando IntelliSense e frammenti di codice.

* Scrivere metodi per la gestione eventi.

Al termine, il programma dovrebbe essere simile all'immagine seguente:

![App visualizzatore immagini creata in questa esercitazione](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

|Titolo|Descrizione|
|-----------|-----------------|
|[Passaggio 1: Creare un progetto di Windows Forms Application](../ide/step-1-create-a-windows-forms-application-project.md)|Iniziare creando un progetto di applicazione Windows Forms.|
|[Passaggio 2: Eseguire l'app](../ide/step-2-run-your-program.md)|Eseguire il programma applicativo Windows Forms creato nel passaggio precedente.|
|[Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md)|Modificare l'aspetto del form usando la finestra **Proprietà**.|
|[Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Aggiungere un oggetto `TableLayoutPanel` al form.|
|[Passaggio 5: Aggiungere controlli al modulo](../ide/step-5-add-controls-to-your-form.md)|Aggiungere controlli, ad esempio un controllo `PictureBox` e un controllo `CheckBox`, al form. Aggiungere pulsanti al form.|
|[Passaggio 6: Assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md)|Rinominare i pulsanti con nomi più significativi.|
|[Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo](../ide/step-7-add-dialog-components-to-your-form.md)|Aggiungere un componente `OpenFileDialog` e un componente `ColorDialog` al modulo.|
|[Passaggio 8: Scrivere il codice per il gestore dell'evento del pulsante Mostra immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Creare codice utilizzando lo strumento IntelliSense.|
|[Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md)|Esaminare e testare il codice. Aggiungere commenti in base alle necessità.|
|[Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Scrivere codice per far funzionare altri pulsanti e una casella di controllo utilizzando IntelliSense.|
|[Passaggio 11: Eseguire il programma e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md)|Eseguire il programma e impostare il colore di sfondo. Provare altre funzionalità, ad esempio la modifica di colori, tipi di carattere e bordi.|

## <a name="next-steps"></a>Passaggi successivi

Per iniziare l'esercitazione, iniziare con  **[il passaggio 1: Creare un progetto](../ide/step-1-create-a-windows-forms-application-project.md)** Windows Forms Application.

## <a name="see-also"></a>Vedere anche

* [Altre C# esercitazioni](/visualstudio/get-started/csharp/)
* [Esercitazioni Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++esercitazioni](../ide/getting-started-with-cpp-in-visual-studio.md)
