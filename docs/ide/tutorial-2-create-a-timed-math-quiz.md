---
title: 'Esercitazione 2: Creare un quiz matematico a tempo'
ms.date: 11/04/2016
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51bda0a85735bf2b1dae5044b9e4ab8e5384f8ae
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987869"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Esercitazione 2: Creare un quiz matematico a tempo

In questa esercitazione si compila un quiz dove l'esecutore deve rispondere a quattro problemi aritmetici casuali entro il tempo specificato. Vengono illustrate le seguenti procedure:

- Generare numeri casuali utilizzando la classe <xref:System.Random>.

- Attivare eventi che devono verificarsi in un momento specifico usando un controllo <xref:System.Windows.Forms.Timer>.

- Controllare il flusso di programma mediante istruzioni `if else`.

- Eseguire operazioni aritmetiche di base nel codice.

Al termine, il quiz sarà simile allo screenshot seguente, ad eccezione dei numeri diversi:

![Quiz matematico con quattro problemi](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

Per scaricare una versione completa del quiz, vedere [Complete Math Quiz tutorial sample](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c) (Esercitazione di esempio completa per un quiz matematico).

> [!NOTE]
> Questa esercitazione illustra sia C# Visual Basic, quindi concentrarsi sulle informazioni specifiche del linguaggio di programmazione che si sta usando.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Passaggio 1: Creare un progetto e aggiungere etichette al modulo](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Iniziare creando il progetto, modificando le proprietà e aggiungendo controlli `Label`.|
|[Passaggio 2: Creare un problema di addizione casuale](../ide/step-2-create-a-random-addition-problem.md)|Creare un problema di addizione e utilizzare la classe `Random` per generare numeri casuali.|
|[Passaggio 3: Aggiungere un timer per il conto alla rovescia](../ide/step-3-add-a-countdown-timer.md)|Aggiungere un timer per il conto alla rovescia in modo che sia possibile impostare una durata per il quiz.|
|[Passaggio 4: Aggiungere il metodo CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Aggiungere un metodo per controllare se l'esecutore del quiz ha immesso una risposta corretta al problema.|
|[Passaggio 5: Aggiungere gestori dell'evento Enter per i controlli NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Aggiungere gestori eventi per semplificare lo svolgimento del quiz.|
|[Passaggio 6: Aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md)|Aggiungere un problema di sottrazione che genera numeri casuali, utilizza il timer e controlla le risposte corrette.|
|[Passaggio 7: Aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md)|Aggiungere problemi di moltiplicazione e divisione che generano numeri casuali, utilizzano il timer e controllano le risposte corrette.|
|[Passaggio 8: Personalizzare il quiz](../ide/step-8-customize-the-quiz.md)|Provare altre funzionalità, ad esempio la modifica dei colori e l'aggiunta di un suggerimento.|
