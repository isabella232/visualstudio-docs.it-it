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
ms.openlocfilehash: 5f1431d56516c749004cef1b35ada482a6c53446
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579719"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Esercitazione 1: Creare un visualizzatore di immagini

In questa esercitazione si compila un'app che carica un'immagine da un file e la visualizza in una finestra. Viene illustrato come utilizzare **Progettazione Windows Form** per trascinare controlli come pulsanti e finestre immagine nel form, impostarne le proprietà e utilizzare i contenitori per ridimensionare il form in modo uniforme. Si inizia inoltre a scrivere il codice.

> [!NOTE]
> In questa esercitazione vengono illustrati sia il linguaggio di programmazione in c'è e Visual Basic, in modo da concentrarsi sulle informazioni specifiche per il linguaggio di programmazione in uso.

Questa esercitazione illustra le attività seguenti:This tutorial walks you through the following tasks:

* Creare un nuovo progetto.

* Testare un'applicazione (eseguirne il debug).

* Aggiungere controlli di base come caselle di controllo e pulsanti a un form.

* Posizionare i controlli in un form utilizzando i layout.

* Aggiungere le finestre di dialogo **Apri file** e **Colore** a un form.

* Scrivere codice utilizzando IntelliSense e frammenti di codice.

* Scrivere metodi per la gestione eventi.

Al termine, l'app dovrebbe essere simile all'immagine seguente:

![App Visualizzatore immagini creata in questa esercitazione](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

|Titolo|Descrizione|
|-----------|-----------------|
|[Passaggio 1: Creare un progetto di app Windows FormStep 1: Create a Windows Forms App project](../ide/step-1-create-a-windows-forms-application-project.md)|Iniziare creando un progetto di app Windows Form.Begin by creating a Windows Forms App project.|
|[Passaggio 2: eseguire l'app Visualizzatore immagini](../ide/step-2-run-your-program.md)|Eseguire il progetto di app Windows Form creato nel passaggio precedente.|
|[Passaggio 3: Impostare le proprietà del modulo](../ide/step-3-set-your-form-properties.md)|Modificare l'aspetto del form usando la finestra **Proprietà**.|
|[Passaggio 4: Disporre il form con un controllo TableLayoutPanelStep 4: Lay out your form with a TableLayoutPanel control](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Aggiungere un oggetto `TableLayoutPanel` al form.|
|[Passaggio 5: Aggiungere controlli al modulo](../ide/step-5-add-controls-to-your-form.md)|Aggiungere controlli, ad esempio un controllo `PictureBox` e un controllo `CheckBox`, al form. Aggiungere pulsanti al form.|
|[Passaggio 6: Assegnare un nome ai controlli dei pulsantiStep 6: Name your button controls](../ide/step-6-name-your-button-controls.md)|Rinominare i pulsanti con nomi più significativi.|
|[Passaggio 7: Aggiungere componenti di finestra di dialogo al modulo](../ide/step-7-add-dialog-components-to-your-form.md)|Aggiungere un componente `OpenFileDialog` e un componente `ColorDialog` al modulo.|
|[Passaggio 8: Scrivere codice per il gestore dell'evento del pulsante Mostra immagine](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Scrivere codice utilizzando lo strumento IntelliSense.Write code by using the IntelliSense tool.|
|[Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md)|Esaminare e testare il codice. Aggiungere commenti in base alle necessità.|
|[Passaggio 10: Scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Scrivere codice per far funzionare altri pulsanti e una casella di controllo utilizzando IntelliSense.|
|[Passaggio 11: Esegui l'app e prova altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md)|Esegui l'app e imposta il colore di sfondo. Provare altre funzionalità, ad esempio la modifica di colori, tipi di carattere e bordi.|

Ci sono anche grandi risorse di apprendimento video gratuite a vostra disposizione. Per ulteriori informazioni sulla programmazione in C, vedere Nozioni di base su [C: Sviluppo per principianti assoluti.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti).

## <a name="next-steps"></a>Passaggi successivi

Per iniziare l'esercitazione, iniziare con **[Passaggio 1: Creare un progetto](../ide/step-1-create-a-windows-forms-application-project.md)** di applicazione Windows Form .

## <a name="see-also"></a>Vedere anche

* [Altre esercitazioni su C](/visualstudio/get-started/csharp/)
* [Esercitazioni su Visual Basic](/visualstudio/get-started/visual-basic/)
* [Esercitazioni in C](/cpp/get-started/tutorial-console-cpp)
