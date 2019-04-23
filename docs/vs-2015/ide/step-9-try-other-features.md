---
title: 'Passaggio 9: Provare altre funzionalità | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 23838c7e68a3da18ba5438a2c56814d6dc27f9b8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102653"
---
# <a name="step-9-try-other-features"></a>Passaggio 9: Provare altre funzionalità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per acquisire maggiore dimestichezza, provare a modificare icone e colori oppure aggiungere un timer di gioco o suoni. Per rendere più impegnativo il gioco, provare a ingrandire la lavagna e a regolare il timer.  
  
 Per scaricare una versione completa dell'esempio, vedere [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Esempio di esercitazione: un gioco delle coppie completo).  
  
### <a name="to-try-other-features"></a>Per provare altre funzionalità  
  
- Sostituire le icone e i colori con altri a piacere.  
  
    > [!TIP]
    >  Osservare la proprietà [ForeColor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) dell'etichetta.  
  
- Aggiungere un timer di gioco per tenere traccia del tempo necessario a un giocatore per vincere.  
  
    > [!TIP]
    >  A tale scopo, è possibile aggiungere un'etichetta per visualizzare il tempo trascorso nel form al di sopra di TableLayoutPanel e aggiungerne un'altra nel form per tenere traccia del tempo. Utilizzare il codice per avviare il timer quando il giocatore inizia la partita e interromperlo dopo che avrà accoppiato le ultime due icone.  
  
- Aggiungere un suono quando il giocatore trova una coppia, un altro suono quando il giocatore scopre due icone che non corrispondono e un terzo suono quando le icone vengono nuovamente nascoste dal programma.  
  
    > [!TIP]
    >  Per riprodurre suoni, è possibile utilizzare lo spazio dei nomi System.media. Per altre informazioni, vedere [Play Sounds in Windows Forms App (C# .NET)](http://youtu.be/qOh4ooHg1UU) (Riprodurre suoni in app di Windows Forms (C# .NET)) o [How To Play Audio In Visual Basic](http://youtu.be/-4oPDeQrtMs) (Come riprodurre suoni in Visual Basic).  
  
- Rendere più difficile il gioco ingrandendo la lavagna.  
  
    > [!TIP]
    >  Non sarà sufficiente aggiungere righe e colonne in TableLayoutPanel: sarà necessario considerare anche il numero di icone da creare.  
  
- Rendere più impegnativo il gioco nascondendo la prima icona se il giocatore è troppo lento a rispondere e non sceglie la seconda icona prima di un determinato periodo di tempo.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
- In caso di blocchi improvvisi o dubbi a livello di programmazione, provare a pubblicare una domanda in uno dei forum MSDN. Vedere il [forum di Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e il [forum di Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
- Sono disponibili utilissime risorse di formazione video gratuite. Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Sviluppo per principianti assoluti](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Per altre informazioni sulla programmazione in oggetto visivo C#, vedere [ C# nozioni fondamentali: Sviluppo per principianti assoluti](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
