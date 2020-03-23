---
title: 'Passaggio 7: Mantenere le coppie visibili'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeca594849625b548857a23b9d5c8e278dcdf07c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579287"
---
# <a name="step-7-keep-pairs-visible"></a>Passaggio 7: Mantenere le coppie visibili
Il gioco funziona finché il giocatore sceglierà coppie di icone che non corrispondono. Si consideri però cosa dovrebbe accadere quando il giocatore sceglie una coppia esatta. Anziché far scomparire le icone attivando il timer, tramite il metodo <xref:System.Windows.Forms.Timer.Start>, il gioco deve reimpostarsi in modo da non tenere più traccia delle etichette tramite le variabili di riferimento `firstClicked` e `secondClicked`, senza reimpostare i colori delle due etichette scelte.

## <a name="to-keep-pairs-visible"></a>Per mantenere le coppie visibili

1. Aggiungere l'istruzione `if` seguente al metodo del gestore eventi `label_Click()`, quasi alla fine del codice, appena prima dell'istruzione di avvio del timer. Esaminare attentamente il codice mentre lo si aggiunge al programma. Considerarne il funzionamento.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     La prima riga dell'istruzione `if` appena aggiunta controlla se l'icona nella prima etichetta scelta dal giocatore è uguale all'icona nella seconda etichetta. Se le icone sono identiche, il programma esegue le tre istruzioni racchiuse tra parentesi graffe in C# o le tre istruzioni all'interno dell'istruzione `if` in Visual Basic. Le prime due istruzioni reimpostano le variabili di riferimento `firstClicked` e `secondClicked` in modo che non tengano più traccia delle etichette. È possibile riconoscere queste due istruzioni dal <xref:System.Windows.Forms.Timer.Tick> gestore eventi del timer. La terza istruzione `return` è un'istruzione, che indica al programma di ignorare il resto delle istruzioni nel metodo senza eseguirle.

     Se si esegue la programmazione in C, è possibile che`=`si sia notato che parte`==`del codice utilizza un segno di uguale singolo ( ), mentre altre istruzioni utilizzano due segni di uguale ( ). Considerare il perché venga utilizzato in alcune occasioni `=`, in altre `==`.

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

     La prima delle due istruzioni controlla se due icone sono uguali. Poiché vengono confrontati due valori, `==` il programma C 'NET utilizza l'operatore di uguaglianza. La seconda istruzione in realtà modifica il valore, detto *assegnazione*, impostando la variabile di riferimento `firstClicked` su `null` per reimpostarla. Per questo viene utilizzato l'operatore di assegnazione `=`. Per impostare i valori `==` e confrontarli, viene utilizzato `=` in C. Visual Basic utilizza `=` sia per l'assegnazione che per il confronto delle variabili.

2. Salvare ed eseguire il programma, quindi iniziare a scegliere icone nel form. Se si sceglie una coppia che non corrisponde, l'evento Tick del timer si attiva ed entrambe le icone scompaiono. Se si sceglie una coppia `if` corrispondente, viene eseguita la nuova istruzione e l'istruzione return fa sì che il metodo salti il codice che avvia il timer, in modo che le icone rimangano visibili, come illustrato nell'immagine seguente.

     ![Gioco creato in questa esercitazione](../ide/media/express_finishedgame.png)<br/>
***Gioco di abbinamento*** con coppie di *icone visibili*

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Aggiungere un timer](../ide/step-6-add-a-timer.md).
