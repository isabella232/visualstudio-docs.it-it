---
title: "Passaggio 11: Eseguire l'app visualizzatore immagini e provare altre funzionalità"
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
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
ms.openlocfilehash: 4d57852a356b2399a358f1636495e96a3dcec44f
ms.sourcegitcommit: 6993bcb0d2b0067b1b7b7899bfba52c31c70b7e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095328"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Passaggio 11: Eseguire l'app visualizzatore immagini e provare altre funzionalità

L'app visualizzatore immagini è stata completata e pronta per l'esecuzione. È possibile eseguire l'app e impostare il colore di sfondo dell' <xref:System.Windows.Forms.PictureBox>oggetto. Per ulteriori informazioni, provare a migliorare l'applicazione modificando il colore del form, personalizzando i pulsanti e la casella di controllo e modificando le proprietà del form.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Come eseguire l'app e impostare il colore di sfondo

1. Premere **F5** oppure scegliere **Debug** > **Avvia debug** sulla barra dei menu.

1. Prima di aprire un'immagine, scegliere il pulsante **Imposta colore di sfondo**. Verrà visualizzata la finestra di dialogo **Colore**.

     ![Finestra di dialogo Colore](../ide/media/express_colordialog.png)<br/>
***Colore*** finestra di *dialogo*

1. Scegliere un colore per impostare il colore di sfondo di PictureBox. Osservare attentamente il metodo `backgroundButton_Click()` (o, `BackgroundButton_Click()`) per comprenderne il funzionamento.

    > [!NOTE]
    > È possibile caricare un'immagine da Internet incollando il relativo URL nella finestra di dialogo **Apri file**. Tentare di trovare un'immagine con uno sfondo trasparente, in modo da visualizzare il colore di sfondo scelto.

1. Scegliere il pulsante **Cancella immagine** per assicurarsi che l'immagine venga cancellata. Uscire quindi dall'app scegliendo il pulsante **Chiudi** .

## <a name="try-other-features"></a>Provare altre funzionalità

* Modificare il colore del form e dei pulsanti tramite la proprietà **BackColor**.

* Personalizzare i pulsanti e la casella di controllo usando le proprietà **Font** e **ForeColor**.

* Modificare le proprietà **FormBorderStyle** e **ControlBox** del form.

* Usare le proprietà **AcceptButton** e **CancelButton** del modulo, affinché i pulsanti vengano scelti automaticamente quando l'utente preme **INVIO** o **ESC**. Fare in modo che l'app apra la finestra di dialogo **Apri file** quando l'utente sceglie **invio** e chiude la casella quando l'utente sceglie **ESC**.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Esercitazione 2: Creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md)

Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Vedere anche

* [Altre C# esercitazioni](/visualstudio/get-started/csharp/)
* [Altre esercitazioni Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++Tutorial](/cpp/get-started/tutorial-console-cpp)
