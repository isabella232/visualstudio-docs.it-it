---
title: "Passaggio 11: Eseguire l'app Visualizzatore immagini e provare altre funzionalità"
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579897"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Passaggio 11: Eseguire l'app Visualizzatore immagini e provare altre funzionalità

L'app visualizzatore di immagini è terminata e pronta per l'esecuzione. È possibile eseguire l'app e <xref:System.Windows.Forms.PictureBox>impostare il colore di sfondo del file . Per ulteriori informazioni, provare a migliorare l'applicazione modificando il colore del modulo, personalizzando i pulsanti e la casella di controllo e modificando le proprietà del modulo.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Come eseguire l'app e impostare il colore di sfondo

1. Premere **F5** oppure scegliere **Debug** > **Avvia debug** sulla barra dei menu.

1. Prima di aprire un'immagine, scegliere il pulsante **Imposta colore di sfondo**. Verrà visualizzata la finestra di dialogo **Colore**.

     ![Finestra di dialogo Colore](../ide/media/express_colordialog.png)<br/>
***Finestra*** *di dialogo* Colore

1. Scegliere un colore per impostare il colore di sfondo di PictureBox. Osservare attentamente `backgroundButton_Click()` il `BackgroundButton_Click()`metodo (o, ) per comprenderne il funzionamento.

    > [!NOTE]
    > È possibile caricare un'immagine da Internet incollando il relativo URL nella finestra di dialogo **Apri file**. Tentare di trovare un'immagine con uno sfondo trasparente, in modo da visualizzare il colore di sfondo scelto.

1. Scegliere il pulsante **Cancella immagine** per assicurarsi che l'immagine venga cancellata. Quindi, uscire dall'app scegliendo il pulsante **Chiudi.**

## <a name="try-other-features"></a>Provare altre funzionalità

* Modificare il colore del form e dei pulsanti tramite la proprietà **BackColor**.

* Personalizzare i pulsanti e la casella di controllo usando le proprietà **Font** e **ForeColor**.

* Modificare le proprietà **FormBorderStyle** e **ControlBox** del form.

* Usare le proprietà **AcceptButton** e **CancelButton** del modulo, affinché i pulsanti vengano scelti automaticamente quando l'utente preme **INVIO** o **ESC**. Fare in modo che l'app apra la finestra di dialogo **Apri file** quando l'utente sceglie **INVIO** e chiude la casella quando l'utente sceglie **ESC**.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, passare all'esercitazione successiva:

> [!div class="nextstepaction"]
> [Esercitazione 2: Creare un quiz di matematica a tempoTutorial 2: Create a timed math quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)

Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 10: Scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Vedere anche

* [Altre esercitazioni su C](/visualstudio/get-started/csharp/)
* [Altre esercitazioni di Visual Basic](/visualstudio/get-started/visual-basic/)
* [Esercitazione su C](/cpp/get-started/tutorial-console-cpp)
