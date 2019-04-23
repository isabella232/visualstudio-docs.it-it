---
title: 'Passaggio 4: Aggiungere il metodo CheckTheAnswer () | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0b2473654bf05a66ef94bd0e88f06ae3e27dbf12
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060540"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Passaggio 4: Aggiungere il metodo CheckTheAnswer()
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella quarta parte di questa esercitazione si scriverà un metodo, `CheckTheAnswer()`, che verifica se le risposte ai problemi di matematica sono corrette. Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Se si utilizza Visual Basic, poiché questo metodo restituisce un valore, anziché la solita parola chiave `Function` si utilizzerà invece la parola chiave `Sub`. È molto semplice: una subroutine non restituisce un valore, ma una funzione sì.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>Per verificare se le risposte sono corrette  
  
1. Aggiungere il metodo `CheckTheAnswer()`.  
  
     Quando viene chiamato, questo metodo aggiunge i valori di addend1 e addend2 e confronta il risultato al valore nel controllo `NumericUpDown` della somma. Se i valori sono uguali, il metodo restituisce il valore `true`. In caso contrario, il metodo restituisce il valore `false`. Il codice dovrebbe essere analogo al seguente.  
  
     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]  
  
     Successivamente, si controllerà la risposta aggiornando il codice nel metodo per il gestore dell'evento Tick del timer per chiamare il nuovo metodo `CheckTheAnswer()`.  
  
2. Aggiungere il codice seguente all'istruzione `if else`:  
  
     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]  
  
     Se la risposta è corretta, `CheckTheAnswer()` restituisce `true`. Il gestore eventi arresta il timer, visualizza un messaggio di congratulazioni e rende quindi nuovamente disponibile il pulsante **Avvio**. In caso contrario, il quiz continua.  
  
3. Salvare il programma, eseguirlo, avviare un quiz e fornire una risposta corretta al problema di addizione.  
  
    > [!NOTE]
    >  Prima di immettere la risposta è necessario selezionare il valore predefinito oppure eliminare manualmente lo zero. Si correggerà questo comportamento più avanti in questa esercitazione.  
  
     Quando si fornisce una risposta corretta, viene aperta una finestra di messaggio, il pulsante **Avvio** diventa disponibile e il timer si arresta.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 5: Aggiungere gestori di eventi Enter per i controlli NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: Aggiungere un Timer del conto alla rovescia](../ide/step-3-add-a-countdown-timer.md).
