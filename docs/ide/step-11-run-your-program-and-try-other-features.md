---
title: Eseguire l'app visualizzatore di immagini e provare altre funzionalità
description: Eseguire l'app visualizzatore di immagini e provare altre funzionalità nell'esercitazione Creare un visualizzatore di immagini.
ms.date: 09/11/2019
ms.custom: SEO-VS-2020
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 39bd1f97408f81b486a7c5f4128c71dca686608f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078115"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Passaggio 11: Eseguire l'app visualizzatore di immagini e provare altre funzionalità

L'app visualizzatore di immagini è stata completata e pronta per l'esecuzione. È possibile eseguire l'app e impostare il colore di sfondo di <xref:System.Windows.Forms.PictureBox> . Per altre informazioni, provare a migliorare l'applicazione modificando il colore del form, personalizzando i pulsanti e la casella di controllo e modificando le proprietà del form.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Come eseguire l'app e impostare il colore di sfondo

1. Premere **F5** oppure scegliere **Debug** > **Avvia debug** sulla barra dei menu.

1. Prima di aprire un'immagine, scegliere il pulsante **Imposta colore di sfondo**. Verrà visualizzata la finestra di dialogo **Colore**.

     ![Finestra di dialogo Colore](../ide/media/express_colordialog.png)<br/>
***Color** _ _dialog box*

1. Scegliere un colore per impostare il colore di sfondo di PictureBox. Esaminare attentamente il `backgroundButton_Click()` metodo (o `BackgroundButton_Click()` ) per comprenderne il funzionamento.

    > [!NOTE]
    > È possibile caricare un'immagine da Internet incollando il relativo URL nella finestra di dialogo **Apri file**. Tentare di trovare un'immagine con uno sfondo trasparente, in modo da visualizzare il colore di sfondo scelto.

1. Scegliere il pulsante **Cancella immagine** per assicurarsi che l'immagine venga cancellata. Uscire quindi dall'app scegliendo il **pulsante** Chiudi.

## <a name="try-other-features"></a>Provare altre funzionalità

* Modificare il colore del form e dei pulsanti tramite la proprietà **BackColor**.

* Personalizzare i pulsanti e la casella di controllo usando le proprietà **Font** e **ForeColor**.

* Modificare le proprietà **FormBorderStyle** e **ControlBox** del form.

* Usare le proprietà **AcceptButton** e **CancelButton** del modulo, affinché i pulsanti vengano scelti automaticamente quando l'utente preme **INVIO** o **ESC**. Fare in modo che **l'app** a  aperti la finestra di dialogo Apri file quando l'utente sceglie INVIO e chiudere la casella quando l'utente sceglie **ESC.**

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, passare all'esercitazione successiva:

> [!div class="nextstepaction"]
> [Esercitazione 2: Creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md)

Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 10: Scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Vedi anche

* [Altre esercitazioni su C#](../get-started/csharp/index.yml)
* [Altre Visual Basic esercitazioni](../get-started/visual-basic/index.yml)
* [Esercitazione su C++](/cpp/get-started/tutorial-console-cpp)