---
title: 'Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto'
description: Scopri come aggiungere un metodo per determinare se il giocatore ha vinto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3857601bc577d2da0fa90d95409ecb1b05218435
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398011"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto
È stato creato un gioco divertente, ma serve un elemento aggiuntivo per completare l'opera. Il gioco deve terminare quando il giocatore vince, pertanto è necessario aggiungere un metodo `CheckForWinner()` per verificare se il giocatore ha vinto.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Per aggiungere un metodo per verificare se il giocatore ha vinto

1. Aggiungere un metodo `CheckForWinner()` alla fine del codice, al di sotto del gestore eventi `timer1_Tick()`, come illustrato nel codice seguente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > Usare il controllo del linguaggio di programmazione in alto a destra in questa pagina per visualizzare il frammento di codice C# o il frammento Visual Basic codice.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     Il metodo usa un `foreach` altro ciclo in C# o un ciclo `For Each` in Visual Basic per scorrere ogni etichetta in <xref:System.Windows.Forms.TableLayoutPanel> . Usa l'operatore di uguaglianza ( in C# e in Visual Basic) per controllare il colore dell'icona di ogni etichetta per verificare se corrisponde `==` `=` allo sfondo. Se i colori corrispondono, l'icona resta invisibile e il giocatore non ha accoppiato tutte le icone rimanenti. In tal caso, il programma utilizza un'istruzione `return` per ignorare la parte restante del metodo. Se il ciclo scorre tutte le etichette senza eseguire l'istruzione `return`, significa che tutte le icone nel form sono state accoppiate. Il programma visualizza un oggetto MessageBox con un messaggio di congratulazioni all'utente, quindi chiama il metodo `Close()` del form per terminare il gioco.

2. Fare quindi in modo che il gestore dell'evento <xref:System.Windows.Forms.Control.Click> dell'etichetta chiami il nuovo metodo `CheckForWinner()`. Accertarsi che il programma verifichi se il giocatore ha vinto immediatamente dopo aver visualizzato la seconda icona scelta dal giocatore. Cercare la riga in cui si è impostato il colore della seconda icona scelta, quindi chiamare il metodo `CheckForWinner()` subito dopo, come illustrato nel codice seguente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. Salvare ed eseguire il programma. Giocare e accoppiare tutte le icone. Quando si vincono, il programma visualizza un **MessageBox** di primo tipo (come illustrato nello screenshot seguente) e quindi chiude la casella.

     ![Gioco di abbinamenti con MessageBox](../ide/media/express_tut4step8.png)<br/>
***Gioco di abbinamenti** _ _with* ***MessageBox***

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 9: Provare altre funzionalità.](../ide/step-9-try-other-features.md)**

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: Mantenere le coppie visibili](../ide/step-7-keep-pairs-visible.md).
