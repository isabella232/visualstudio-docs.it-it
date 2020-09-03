---
title: 'Passaggio 11: eseguire il programma e provare altre funzionalità | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bff0467cfe9447b1cc7814d471f56ab323bb853d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851586"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Passaggio 11: eseguire il programma e provare altre funzionalità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il programma è stato completato ed è pronto per l'esecuzione. È possibile eseguire il programma e impostare il colore di sfondo di PictureBox. Per continuare a esercitarsi, provare a migliorare il programma modificando il colore del form, personalizzando i pulsanti e la casella di controllo e modificando le proprietà del form.

 ![collegamento al video](../data-tools/media/playvideo.gif "PlayVideo") Per una versione video di questo argomento, vedere [esercitazione 1: creare un visualizzatore immagini in Visual Basic-video 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) o [esercitazione 1: creare un visualizzatore immagini in C#-video 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.

### <a name="to-run-your-program-and-set-the-background-color"></a>Per eseguire il programma e impostare il colore di sfondo

1. Premere F5 o scegliere **Debug**, **Avvia debug** dalla barra dei menu.

2. Prima di aprire un'immagine, scegliere il pulsante **Imposta colore di sfondo**. Verrà visualizzata la finestra di dialogo **Colore**.

     Finestra di ![dialogo colore](../ide/media/express-colordialog.png "Express_ColorDialog") Finestra di dialogo colore

3. Scegliere un colore per impostare il colore di sfondo di PictureBox. Analizzare attentamente il metodo `backgroundButton_Click()` per capirne il funzionamento.

    > [!NOTE]
    > È possibile caricare un'immagine da Internet incollando il relativo URL nella finestra di dialogo **Apri file**. Tentare di trovare un'immagine con uno sfondo trasparente, in modo da visualizzare il colore di sfondo scelto.

4. Scegliere il pulsante **Cancella immagine** per assicurarsi che l'immagine venga cancellata. Uscire quindi dal programma scegliendo il pulsante **Chiudi**.

### <a name="to-try-other-features"></a>Per provare altre funzionalità

- Modificare il colore del form e dei pulsanti tramite la proprietà **BackColor**.

- Personalizzare i pulsanti e la casella di controllo usando le proprietà **Font** e **ForeColor**.

- Modificare le proprietà **FormBorderStyle** e **ControlBox** del form.

- Usare le proprietà **AcceptButton** e **CancelButton** del form in modo che i pulsanti vengano scelti automaticamente quando l'utente sceglie il tasto invio o ESC. Fare in modo che il programma apra la finestra di dialogo **Apri file** quando l'utente sceglie invio e chiude la casella quando l'utente sceglie ESC.

### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per altre informazioni sulla programmazione in Visual Studio, vedere [concetti relativi alla programmazione](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).

- Per altre informazioni su Visual Basic, vedere [Sviluppo di applicazioni con Visual Basic](https://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).

- Per ulteriori informazioni su Visual C#, vedere [Introduzione al linguaggio C# e al .NET Framework](https://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).

- Per passare all'esercitazione successiva, vedere [esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).

- Per tornare al passaggio precedente dell'esercitazione, vedere [passaggio 10: scrivere codice per pulsanti aggiuntivi e una casella di controllo](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
