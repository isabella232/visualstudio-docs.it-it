---
title: 'Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579432"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi

Ora si è pronti per completare gli altri quattro metodi. È possibile copiare e incollare questo codice, ma se si desidera ottenere il massimo vantaggio da questa esercitazione, digitare il codice e utilizzare IntelliSense.

Con questo codice si aggiungono funzionalità ai pulsanti aggiunti in precedenza. Senza questo codice i pulsanti non eseguono alcuna operazione. I pulsanti utilizzano il codice nei relativi eventi <xref:System.Windows.Forms.Control.Click> (la casella di controllo utilizza l'evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>) per eseguire operazioni diverse quando si attivano i controlli. Ad esempio, l' `clearButton_Click` evento ( `ClearButton_Click` o), che si attiva quando si sceglie il **pulsante Cancella immagine** , cancella l'immagine corrente impostando la relativa proprietà **Image** su **null** (o, **Nothing**). Ogni evento nel codice include commenti che spiegano l'azione eseguita dal codice.

> [!TIP]
> Come procedura consigliata, commentare sempre il codice. I commenti contengono informazioni destinate a una persona ed è consigliabile aggiungerli per rendere comprensibile il codice. Tutto ciò che si trova su una riga di commento viene ignorato dall'app. In C# si commenta una riga digitando due barre all'inizio (//) e in Visual Basic si commenta una riga iniziando con una virgoletta singola (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Come scrivere codice per pulsanti aggiuntivi e una casella di controllo

Aggiungere il codice seguente al file di codice **Form1** (*Form1.cs* o *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Il codice potrebbe non visualizzare le lettere "camelCase".

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 11: eseguire l'app e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
