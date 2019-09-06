---
title: 'Passaggio 11: Eseguire il programma e provare altre funzionalità'
ms.date: 08/30/2019
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
ms.openlocfilehash: 5486aa4d2effa3feb03b31bace7a9cfc86fd9925
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293599"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Passaggio 11: Eseguire il programma e provare altre funzionalità

Il programma è stato completato ed è pronto per l'esecuzione. È possibile eseguire il programma e impostare il colore di sfondo di <xref:System.Windows.Forms.PictureBox>. Per continuare a esercitarsi, provare a migliorare il programma modificando il colore del form, personalizzando i pulsanti e la casella di controllo e modificando le proprietà del form.

## <a name="how-to-run-your-program-and-set-the-background-color"></a>Come eseguire il programma e impostare il colore di sfondo

1. Premere **F5** oppure scegliere **Debug** > **Avvia debug** sulla barra dei menu.

1. Prima di aprire un'immagine, scegliere il pulsante **Imposta colore di sfondo**. Verrà visualizzata la finestra di dialogo **Colore**.

     ![Finestra di dialogo Colore](../ide/media/express_colordialog.png)<br/>
***Colore*** finestra di *dialogo*

1. Scegliere un colore per impostare il colore di sfondo di PictureBox. Osservare attentamente il metodo `backgroundButton_Click()` (o, `BackgroundButton_Click()`) per comprenderne il funzionamento.

    > [!NOTE]
    > È possibile caricare un'immagine da Internet incollando il relativo URL nella finestra di dialogo **Apri file**. Tentare di trovare un'immagine con uno sfondo trasparente, in modo da visualizzare il colore di sfondo scelto.

1. Scegliere il pulsante **Cancella immagine** per assicurarsi che l'immagine venga cancellata. Uscire quindi dal programma scegliendo il pulsante **Chiudi**.

## <a name="try-other-features"></a>Provare altre funzionalità

* Modificare il colore del form e dei pulsanti tramite la proprietà **BackColor**.

* Personalizzare i pulsanti e la casella di controllo usando le proprietà **Font** e **ForeColor**.

* Modificare le proprietà **FormBorderStyle** e **ControlBox** del form.

* Usare le proprietà **AcceptButton** e **CancelButton** del modulo, affinché i pulsanti vengano scelti automaticamente quando l'utente preme **INVIO** o **ESC**. Configurare il programma in modo da aprire la finestra di dialogo **Apri file** quando l'utente preme **INVIO** e chiuderla quando l'utente preme **ESC**.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Esercitazione 2: Creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md)

Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Vedere anche

* [Altre C# esercitazioni](/visualstudio/get-started/csharp/)
* [Altre esercitazioni Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++Tutorial](../ide/getting-started-with-cpp-in-visual-studio.md)
