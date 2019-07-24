---
title: 'Passaggio 7: Mantenere le coppie visibili'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5194d3925393228d951f35a966dff8fd620ea924
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416522"
---
# <a name="step-7-keep-pairs-visible"></a>Passaggio 7: Mantenere le coppie visibili
Il gioco funziona finché il giocatore sceglierà coppie di icone che non corrispondono. Si consideri però cosa dovrebbe accadere quando il giocatore sceglie una coppia esatta. Anziché far scomparire le icone attivando il timer, tramite il metodo <xref:System.Windows.Forms.Timer.Start>, il gioco deve reimpostarsi in modo da non tenere più traccia delle etichette tramite le variabili di riferimento `firstClicked` e `secondClicked`, senza reimpostare i colori delle due etichette scelte.

## <a name="to-keep-pairs-visible"></a>Per mantenere le coppie visibili

1. Aggiungere l'istruzione `if` seguente al metodo del gestore eventi `label_Click()`, quasi alla fine del codice, appena prima dell'istruzione di avvio del timer. Esaminare attentamente il codice mentre lo si aggiunge al programma. Considerarne il funzionamento.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     La prima riga dell'istruzione `if` appena aggiunta controlla se l'icona nella prima etichetta scelta dal giocatore è uguale all'icona nella seconda etichetta. Se le icone sono identiche, il programma esegue le tre istruzioni racchiuse tra parentesi graffe in C# o le tre istruzioni all'interno dell'istruzione `if` in Visual Basic. Le prime due istruzioni reimpostano le variabili di riferimento `firstClicked` e `secondClicked` in modo che non tengano più traccia delle etichette. È possibile riconoscere le due istruzioni dal gestore dell'evento <xref:System.Windows.Forms.Timer.Tick> del timer. La terza istruzione è un'istruzione `return` che indica al programma di ignorare e non eseguire le istruzioni restanti nel metodo.

     Se si esegue la programmazione in Visual C#, si può notare come parte del codice utilizzi un unico segno di uguale (`=`), mentre altre istruzioni utilizzano due segni di uguale (`==`). Considerare il perché venga utilizzato in alcune occasioni `=`, in altre `==`.

     Questo è un ottimo esempio per comprendere la differenza. Esaminare attentamente il codice tra parentesi nell'istruzione `if`.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Osservare quindi attentamente la prima istruzione nel blocco di codice dopo l'istruzione `if`.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     La prima delle due istruzioni controlla se due icone sono uguali. Poiché vengono confrontati due valori, il programma Visual C# utilizza l'operatore di uguaglianza `==`. La seconda istruzione in realtà modifica il valore, detto *assegnazione*, impostando la variabile di riferimento `firstClicked` su `null` per reimpostarla. Per questo viene utilizzato l'operatore di assegnazione `=`. Visual C# utilizza `=` per impostare valori e `==` per confrontarli. Visual Basic utilizza `=` sia per l'assegnazione che per il confronto delle variabili.

2. Salvare ed eseguire il programma, quindi iniziare a scegliere icone nel form. Se si sceglie una coppia che non corrisponde, l'evento Tick del timer si attiva ed entrambe le icone scompaiono. Se si sceglie una coppia esatta, la nuova istruzione `if` viene eseguita e l'istruzione return fa sì che il metodo ignori il codice di avvio del timer, in modo che le icone restino visibili, come mostrato nell'immagine seguente.

     ![Gioco creato in questa esercitazione](../ide/media/express_finishedgame.png)
**Gioco di abbinamenti** con coppie di icone visibili

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Aggiungere un timer](../ide/step-6-add-a-timer.md).
