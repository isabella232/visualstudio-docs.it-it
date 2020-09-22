---
title: 'Esercitazione 1: Creare un visualizzatore di immagini'
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44fe22aa1d4549d1daba4324349160afcd3133ba
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811214"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Esercitazione 1: Creare un visualizzatore di immagini

In questa esercitazione viene compilata un'app che carica un'immagine da un file e la Visualizza in una finestra. Si apprenderà come usare il **Progettazione Windows Form** per trascinare controlli quali pulsanti e caselle immagine nel form, impostarne le proprietà e usare i contenitori per ridimensionare il form in modo uniforme. Si inizia inoltre a scrivere il codice.

> [!NOTE]
> Questa esercitazione illustra sia C# che Visual Basic, quindi concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.

Questa esercitazione illustra le attività seguenti:

* Creare un nuovo progetto.

* Testare un'applicazione (eseguirne il debug).

* Aggiungere controlli di base come caselle di controllo e pulsanti a un form.

* Posizionare i controlli in un form utilizzando i layout.

* Aggiungere le finestre di dialogo **Apri file** e **Colore** a un form.

* Scrivere codice usando IntelliSense e frammenti di codice.

* Scrivere metodi per la gestione eventi.

Al termine, l'app dovrebbe avere un aspetto simile all'immagine seguente:

![App visualizzatore immagini creata in questa esercitazione](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

|Titolo|Descrizione|
|-----------|-----------------|
|[Passaggio 1: Creare un progetto di app Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Per iniziare, creare un progetto di app Windows Forms.|
|[Passaggio 2: eseguire l'app visualizzatore immagini](../ide/step-2-run-your-program.md)|Eseguire il progetto di app Windows Forms creato nel passaggio precedente.|
|[Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md)|Modificare l'aspetto del form usando la finestra **Proprietà**.|
|[Passaggio 4: Creare il layout del modulo con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Aggiungere un oggetto `TableLayoutPanel` al form.|
|[Passaggio 5: Aggiungere controlli al modulo](../ide/step-5-add-controls-to-your-form.md)|Aggiungere controlli, ad esempio un controllo `PictureBox` e un controllo `CheckBox`, al form. Aggiungere pulsanti al form.|
|[Passaggio 6: Assegnare un nome ai pulsanti](../ide/step-6-name-your-button-controls.md)|Rinominare i pulsanti con nomi più significativi.|
|[Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo](../ide/step-7-add-dialog-components-to-your-form.md)|Aggiungere un componente `OpenFileDialog` e un componente `ColorDialog` al modulo.|
|[Passaggio 8: scrivere il codice per il gestore dell'evento del pulsante Visualizza immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Scrivere codice utilizzando lo strumento IntelliSense.|
|[Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md)|Esaminare e testare il codice. Aggiungere commenti in base alle necessità.|
|[Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Scrivere codice per far funzionare altri pulsanti e una casella di controllo utilizzando IntelliSense.|
|[Passaggio 11: Eseguire l'app e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md)|Eseguire l'app e impostare il colore di sfondo. Provare altre funzionalità, ad esempio la modifica di colori, tipi di carattere e bordi.|

Sono disponibili anche eccezionali risorse di formazione video gratuite. Per altre informazioni sulla programmazione in C#, vedere [nozioni fondamentali su c#: sviluppo per principianti assoluti](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti).

## <a name="next-steps"></a>Passaggi successivi

Per iniziare l'esercitazione, iniziare con il **[passaggio 1: creare un Windows Forms Application progetto](../ide/step-1-create-a-windows-forms-application-project.md)**.

## <a name="see-also"></a>Vedere anche

* [Altre esercitazioni su C#](../get-started/csharp/index.yml)
* [Esercitazioni Visual Basic](../get-started/visual-basic/index.yml)
* [Esercitazioni su C++](/cpp/get-started/tutorial-console-cpp)