---
title: 'Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19c82238a0379e6b94e82bb1e34f20282ff4654f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930168"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi
Ora si è pronti per completare gli altri quattro metodi. È possibile copiare e incollare questo codice, ma se si desidera ottenere il massimo vantaggio da questa esercitazione, digitare il codice e utilizzare IntelliSense.

 Con questo codice si aggiungono funzionalità ai pulsanti aggiunti in precedenza. Senza questo codice i pulsanti non eseguono alcuna operazione. I pulsanti utilizzano il codice nei relativi eventi <xref:System.Windows.Forms.Control.Click> (la casella di controllo utilizza l'evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>) per eseguire operazioni diverse quando si attivano i controlli. Ad esempio l'evento `clearButton_Click`, che si attiva quando si sceglie il pulsante **Cancella immagine**, cancella l'immagine corrente impostando la proprietà **Image** su **null** (o **nothing**). Ogni evento nel codice include commenti che spiegano l'azione eseguita dal codice.

 ![Collegamento a video](../data-tools/media/playvideo.gif)Per una versione video di questo argomento, vedere [Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) o [Esercitazione 1: Creare un visualizzatore immagini in C# - Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.

> [!NOTE]
>  Procedura consigliata: commentare sempre il codice. I commenti contengono informazioni destinate a una persona ed è consigliabile aggiungerli per rendere comprensibile il codice. Tutto ciò che si trova su una riga di commento viene ignorato dal programma. In Visual C# si commenta una riga digitando due barre all'inizio (//), mentre in Visual Basic si commenta una riga anteponendovi una virgoletta singola (').

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Per scrivere codice per una casella di controllo e pulsanti aggiuntivi

-   Aggiungere il codice seguente al file di codice **Form1** (*Form1.cs* o *Form1.vb*). Scegliere la scheda **VB** per visualizzare il codice Visual Basic.

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

-   Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 11: Eseguire il programma e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md).

-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md).
