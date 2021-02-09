---
title: 'Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto'
description: Informazioni su come aggiungere un metodo per determinare se il giocatore ha vinto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68a4848f00153206b87dd3e5893bbaaeccf3b358
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868751"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto
È stato creato un gioco divertente, ma serve un elemento aggiuntivo per completare l'opera. Il gioco deve terminare quando il giocatore vince, pertanto è necessario aggiungere un metodo `CheckForWinner()` per verificare se il giocatore ha vinto.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Per aggiungere un metodo per verificare se il giocatore ha vinto

1. Aggiungere un metodo `CheckForWinner()` alla fine del codice, al di sotto del gestore eventi `timer1_Tick()`, come illustrato nel codice seguente.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Usare il controllo linguaggio di programmazione nella parte superiore destra della pagina per visualizzare il frammento di codice C# o il frammento di codice Visual Basic.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     Il metodo usa un altro `foreach` ciclo in C# o `For Each` loop in Visual Basic per scorrere ogni etichetta in <xref:System.Windows.Forms.TableLayoutPanel> . Usa l'operatore di uguaglianza ( `==` in C# e `=` in Visual Basic) per controllare il colore dell'icona di ogni etichetta per verificare se corrisponde allo sfondo. Se i colori corrispondono, l'icona resta invisibile e il giocatore non ha accoppiato tutte le icone rimanenti. In tal caso, il programma utilizza un'istruzione `return` per ignorare la parte restante del metodo. Se il ciclo scorre tutte le etichette senza eseguire l'istruzione `return`, significa che tutte le icone nel form sono state accoppiate. Il programma visualizza un oggetto MessageBox con un messaggio di congratulazioni all'utente, quindi chiama il metodo `Close()` del form per terminare il gioco.

2. Fare quindi in modo che il gestore dell'evento <xref:System.Windows.Forms.Control.Click> dell'etichetta chiami il nuovo metodo `CheckForWinner()`. Accertarsi che il programma verifichi se il giocatore ha vinto immediatamente dopo aver visualizzato la seconda icona scelta dal giocatore. Cercare la riga in cui si è impostato il colore della seconda icona scelta, quindi chiamare il metodo `CheckForWinner()` subito dopo, come illustrato nel codice seguente.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Salvare ed eseguire il programma. Giocare e accoppiare tutte le icone. Quando si vince, il programma visualizza un **MessageBox** di congratulazioni, come illustrato nello screenshot seguente, e quindi chiude la finestra.

     ![Gioco di abbinamenti con MessageBox](../ide/media/express_tut4step8.png)<br/>
***Gioco corrispondente** _ _With * ***MessageBox***

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 9: provare altre funzionalità](../ide/step-9-try-other-features.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: Mantenere le coppie visibili](../ide/step-7-keep-pairs-visible.md).
