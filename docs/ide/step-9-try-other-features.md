---
title: 'Passaggio 9: Provare altre funzionalità'
description: Informazioni su come modificare icone e colori, aggiungere un timer di gioco, aggiungere suoni e ingrandire il tabellone di gioco.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6f542c2fe86b642a1d8cf53d9fe1bff4af611c9e
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397668"
---
# <a name="step-9-try-other-features"></a>Passaggio 9: Provare altre funzionalità
Per acquisire maggiore dimestichezza, provare a modificare icone e colori oppure aggiungere un timer di gioco o suoni. Per rendere più impegnativo il gioco, provare a ingrandire la lavagna e a regolare il timer.

Per scaricare una versione completa dell'esempio, vedere l'esempio di esercitazione [completa sul gioco di abbinamenti.](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba)

## <a name="to-try-other-features"></a>Per provare altre funzionalità

- Sostituire le icone e i colori con altri a piacere.

    > [!TIP]
    > Osservare la proprietà [ForeColor](<xref:System.Windows.Forms.Control.ForeColor%2A>) dell'etichetta.

- Aggiungere un timer di gioco per tenere traccia del tempo necessario a un giocatore per vincere.

    > [!TIP]
    > A tale scopo, è possibile aggiungere un'etichetta per visualizzare il tempo trascorso nel modulo al di sopra di <xref:System.Windows.Forms.TableLayoutPanel> e aggiungere un altro timer nel modulo per tenere traccia del tempo. Utilizzare il codice per avviare il timer quando il giocatore inizia la partita e interromperlo dopo che avrà accoppiato le ultime due icone.

- Aggiungere un suono quando il giocatore trova una coppia, un altro suono quando il giocatore scopre due icone che non corrispondono e un terzo suono quando le icone vengono nuovamente nascoste dal programma.

    > [!TIP]
    > Per riprodurre suoni, è possibile usare lo spazio dei nomi <xref:System.Media>. Per altre informazioni, vedere [Play sounds in Windows Forms app (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be)(Riprodurre suoni in app di Windows Forms - C#) o [How to play audio in Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) (Come riprodurre audio in Visual Basic).

- Rendere più difficile il gioco ingrandendo la lavagna.

    > [!TIP]
    > Non sarà sufficiente aggiungere righe e colonne in TableLayoutPanel: sarà necessario considerare anche il numero di icone da creare.

- Rendere più impegnativo il gioco nascondendo la prima icona se il giocatore è troppo lento a rispondere e non sceglie la seconda icona prima di un determinato periodo di tempo.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Sono disponibili utilissime risorse di formazione video gratuite. Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti). Per altre informazioni sulla programmazione in C#, vedere [Nozioni fondamentali su C#: Sviluppo per principianti assoluti.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
