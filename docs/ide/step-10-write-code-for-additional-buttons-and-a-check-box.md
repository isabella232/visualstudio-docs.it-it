---
title: 'Passaggio 10: Scrivere codice per pulsanti aggiuntivi e una casella di controllo'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579432"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Passaggio 10: Scrivere codice per pulsanti aggiuntivi e una casella di controllo

Ora si è pronti per completare gli altri quattro metodi. È possibile copiare e incollare questo codice, ma se si desidera ottenere il massimo vantaggio da questa esercitazione, digitare il codice e utilizzare IntelliSense.

Con questo codice si aggiungono funzionalità ai pulsanti aggiunti in precedenza. Senza questo codice i pulsanti non eseguono alcuna operazione. I pulsanti utilizzano il codice nei relativi eventi <xref:System.Windows.Forms.Control.Click> (la casella di controllo utilizza l'evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>) per eseguire operazioni diverse quando si attivano i controlli. Ad esempio, `clearButton_Click` `ClearButton_Click`l'evento (o ), che si attiva quando si sceglie il pulsante **Cancella l'immagine,** cancella l'immagine corrente impostando la relativa proprietà **Image su** **null** (o **nulla).** Ogni evento nel codice include commenti che spiegano l'azione eseguita dal codice.

> [!TIP]
> Come procedura consigliata, commentare sempre il codice. I commenti contengono informazioni destinate a una persona ed è consigliabile aggiungerli per rendere comprensibile il codice. Tutto ciò che si trova in una riga di commento viene ignorato dall'app. In C, si commenta una riga digitando due barre all'inizio (//) e in Visual Basic si commenta una riga iniziando con una virgoletta singola (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Come scrivere codice per pulsanti aggiuntivi e una casella di controllo

Aggiungere il codice seguente al file di codice **Form1** (*Form1.cs* o *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Il codice potrebbe non visualizzare lettere "camelCase".

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 11: Eseguire l'app e provare altre funzionalità.](../ide/step-11-run-your-program-and-try-other-features.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: Creare un quiz di matematica a tempoTutorial 2: Create a timed math quiz](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
