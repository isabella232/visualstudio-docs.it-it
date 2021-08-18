---
title: Scrivere codice per una casella di controllo e pulsanti aggiuntivi
description: Informazioni su come scrivere codice per pulsanti aggiuntivi e una casella di controllo nell'esercitazione creare un visualizzatore di immagini.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2662c9bd256b69d7698a31ec7dfd71ef6752b67b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123606"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Passaggio 10: Scrivere codice per una casella di controllo e pulsanti aggiuntivi

Ora si è pronti per completare gli altri quattro metodi. È possibile copiare e incollare questo codice, ma se si desidera ottenere il massimo vantaggio da questa esercitazione, digitare il codice e utilizzare IntelliSense.

Con questo codice si aggiungono funzionalità ai pulsanti aggiunti in precedenza. Senza questo codice i pulsanti non eseguono alcuna operazione. I pulsanti utilizzano il codice nei relativi eventi <xref:System.Windows.Forms.Control.Click> (la casella di controllo utilizza l'evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>) per eseguire operazioni diverse quando si attivano i controlli. Ad esempio, l'evento (o ), che si attiva quando si sceglie il pulsante Cancella immagine, cancella l'immagine corrente impostandone la proprietà `clearButton_Click` `ClearButton_Click` **Image** su **Null** (o, **niente).**  Ogni evento nel codice include commenti che spiegano l'azione eseguita dal codice.

> [!TIP]
> Come procedura consigliata, commentare sempre il codice. I commenti contengono informazioni destinate a una persona ed è consigliabile aggiungerli per rendere comprensibile il codice. Tutto ciò che si trova in una riga di commento viene ignorato dall'app. In C# si commenta una riga digitando due barre all'inizio (//) e in Visual Basic si commenta una riga iniziando con una virgoletta singola (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Come scrivere codice per pulsanti aggiuntivi e una casella di controllo

Aggiungere il codice seguente al file di codice **Form1** (*Form1.cs* o *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet2":::

  :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet2":::

> [!NOTE]
> Il codice potrebbe non visualizzare lettere "camelCase".

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 11: Eseguire l'app e provare altre funzionalità.](../ide/step-11-run-your-program-and-try-other-features.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 9: Esaminare, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
