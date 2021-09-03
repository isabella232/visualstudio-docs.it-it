---
title: 'Passaggio 4: Aggiungere il metodo CheckTheAnswer()'
description: Informazioni su come scrivere un metodo CheckTheAnswer()per determinare se le risposte ai problemi matematici sono corrette.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e5f8d7a0c4856a9ff65d99512cf686ad80113d9b
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398626"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Passaggio 4: Aggiungere il metodo CheckTheAnswer()

Nella quarta parte di questa esercitazione si scriverà un metodo, `CheckTheAnswer()`, che verifica se le risposte ai problemi di matematica sono corrette. Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico](../ide/tutorial-2-create-a-timed-math-quiz.md)a tempo.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico](../ide/tutorial-2-create-a-timed-math-quiz.md)a tempo.

## <a name="to-verify-whether-the-answers-are-correct"></a>Per verificare se le risposte sono corrette

> [!NOTE]
> Se si utilizza Visual Basic, poiché questo metodo restituisce un valore, anziché la solita parola chiave `Function` si utilizzerà invece la parola chiave `Sub`. È molto semplice: una subroutine non restituisce un valore, ma una funzione sì.

1. Aggiungere il metodo `CheckTheAnswer()`. Questo metodo deve essere in linea con gli altri metodi effettuati, ad esempio `StartTheQuiz()` .

     Quando viene chiamato, questo metodo aggiunge i valori di addend1 e addend2 e confronta il risultato al valore nel controllo <xref:System.Windows.Forms.NumericUpDown> della somma. Se i valori sono uguali, il metodo restituisce il valore `true`. In caso contrario, il metodo restituisce il valore `false`. Il codice dovrebbe essere analogo al seguente.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet8":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Successivamente, si controllerà la risposta aggiornando il codice nel metodo per il gestore dell'evento <xref:System.Windows.Forms.Timer.Tick> del timer per chiamare il nuovo metodo `CheckTheAnswer()`.

2. Aggiungere il codice seguente all'istruzione nel metodo , in modo che il timer si `if else` `Timer1_Tick()` arresti quando l'utente ottiene la risposta corretta.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet10":::

     Se la risposta è corretta, `CheckTheAnswer()` restituisce `true`. Il gestore eventi arresta il timer, visualizza un messaggio di congratulazioni e rende quindi nuovamente disponibile il pulsante **Avvio**. In caso contrario, il quiz continua.

3. Salvare il programma, eseguirlo, avviare un quiz e fornire una risposta corretta al problema di addizione.

    > [!NOTE]
    > Prima di immettere la risposta è necessario selezionare il valore predefinito oppure eliminare manualmente lo zero. Si correggerà questo comportamento più avanti in questa esercitazione.

     Quando si fornisce una risposta corretta, viene aperta una finestra di messaggio, il pulsante **Avvio** diventa disponibile e il timer si arresta.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere Passaggio 5: Aggiungere gestori eventi **[Enter per i controlli NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: aggiungere un timer per il conto alla rovescia](../ide/step-3-add-a-countdown-timer.md).
