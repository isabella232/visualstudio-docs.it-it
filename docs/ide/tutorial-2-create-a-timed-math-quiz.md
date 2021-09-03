---
title: 'Esercitazione 2: Creare un quiz matematico a tempo'
description: Informazioni su come creare un quiz in cui il quiz deve rispondere a quattro problemi aritmetici casuali entro un tempo specificato.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3beb11ceeb0cb54ecbd923ff808a2ee5506f2b31
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398613"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Esercitazione 2: Creare un quiz matematico a tempo

In questa esercitazione si compila un quiz dove l'esecutore deve rispondere a quattro problemi aritmetici casuali entro il tempo specificato.

> [!NOTE]
> Questa esercitazione illustra sia C# che Visual Basic, quindi concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.

Questa esercitazione illustra le attività seguenti:

- Generare numeri casuali utilizzando la classe <xref:System.Random>.

- Attivare eventi che devono verificarsi in un momento specifico usando un controllo <xref:System.Windows.Forms.Timer>.

- Controllare il flusso di programma mediante istruzioni `if else`.

- Eseguire operazioni aritmetiche di base nel codice.

Al termine, il quiz sarà simile allo screenshot seguente, ad eccezione di numeri diversi:

![Quiz matematico con quattro problemi](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Collegamenti dell'esercitazione

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

Sono disponibili anche risorse di video learning gratuite. Per altre informazioni sulla programmazione in C#, vedere [Nozioni fondamentali di C#: Sviluppo per principianti assoluti.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti).

## <a name="next-steps"></a>Passaggi successivi

Per iniziare l'esercitazione, iniziare **[con Passaggio 1: Creare un progetto e aggiungere etichette al modulo](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**.

## <a name="see-also"></a>Vedi anche

* [Altre esercitazioni su C#](../get-started/csharp/index.yml)
* [Visual Basic esercitazioni](../get-started/visual-basic/index.yml)
* [Esercitazioni su C++](/cpp/get-started/tutorial-console-cpp)