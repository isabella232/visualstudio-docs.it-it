---
title: 'Passaggio 9: Provare altre funzionalità'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc842af3723a8b056d1de684bd798f4fda37cff8
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2018
ms.locfileid: "32065078"
---
# <a name="step-9-try-other-features"></a>Passaggio 9: Provare altre funzionalità
Per acquisire maggiore dimestichezza, provare a modificare icone e colori oppure aggiungere un timer di gioco o suoni. Per rendere più impegnativo il gioco, provare a ingrandire la lavagna e a regolare il timer.  
  
 Per scaricare una versione completa dell'esempio, vedere [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Esercitazione di esempio completa per il gioco di abbinamenti).  
  
## <a name="to-try-other-features"></a>Per provare altre funzionalità  

-   Sostituire le icone e i colori con altri a piacere.  

    > [!TIP]
    >  Osservare la proprietà [ForeColor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) dell'etichetta.  

-   Aggiungere un timer di gioco per tenere traccia del tempo necessario a un giocatore per vincere.  

    > [!TIP]
    >  A tale scopo, è possibile aggiungere un'etichetta per visualizzare il tempo trascorso nel modulo al di sopra di <xref:System.Windows.Forms.TableLayoutPanel> e aggiungere un altro timer nel modulo per tenere traccia del tempo. Utilizzare il codice per avviare il timer quando il giocatore inizia la partita e interromperlo dopo che avrà accoppiato le ultime due icone.  

-   Aggiungere un suono quando il giocatore trova una coppia, un altro suono quando il giocatore scopre due icone che non corrispondono e un terzo suono quando le icone vengono nuovamente nascoste dal programma.  

    > [!TIP]
    >  Per riprodurre suoni, è possibile usare lo spazio dei nomi <xref:System.Media>. Per altre informazioni, vedere [Play sounds in Windows Forms app (C#)](http://youtu.be/qOh4ooHg1UU)(Riprodurre suoni in app di Windows Forms - C#) o [How to play audio in Visual Basic](http://youtu.be/-4oPDeQrtMs) (Come riprodurre audio in Visual Basic).  
  
-   Rendere più difficile il gioco ingrandendo la lavagna.  

    > [!TIP]
    >  Non sarà sufficiente aggiungere righe e colonne in TableLayoutPanel: sarà necessario considerare anche il numero di icone da creare.  

-   Rendere più impegnativo il gioco nascondendo la prima icona se il giocatore è troppo lento a rispondere e non sceglie la seconda icona prima di un determinato periodo di tempo.  

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   In caso di blocchi improvvisi o dubbi a livello di programmazione, provare a pubblicare una domanda in uno dei forum MSDN. Vedere il [forum di Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e il [forum di Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Sono disponibili utilissime risorse di formazione video gratuite. Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti). Per altre informazioni sulla programmazione in Visual C#, vedere [C# Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Nozioni fondamentali di C#: sviluppo per principianti assoluti).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
