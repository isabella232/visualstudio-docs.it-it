---
title: 'Procedura: Ripristinare il refactoring di frammenti C# | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13867274ace5582b25482868ddd3642426b1f295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526013"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Procedura: ripristinare refactoring di frammenti C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: ripristinare Refactoring di frammenti c#](https://docs.microsoft.com/visualstudio/ide/how-to-restore-csharp-refactoring-snippets).  
  
Le operazioni di refactoring di C# si basano sui frammenti di codice disponibili nella directory seguente:  
  
 *Directory di installazione*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID linguaggio*\Refactoring  
  
 Se la directory Refactoring o i file in questa directory vengono eliminati o danneggiati, le operazioni di refactoring di C# potrebbero non funzionare nell'IDE. Le procedure seguenti consentono di ripristinare i frammenti di codice per il refactoring di C#.   
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Per verificare la disponibilità di frammenti di codice per il refactoring di C# tramite Gestione frammenti di codice  
  
1.  Scegliere **Gestione frammenti di codice** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Gestione frammenti di codice** selezionare **Visual C#** nell'elenco a discesa **Linguaggio**.  
  
     Nell'elenco di cartelle della visualizzazione albero dovrebbe essere visualizzata una cartella **Refactoring**.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Per ripristinare il refactoring vedere il commento in Gestione frammenti di codice  
  
1.  Se la cartella **Refactoring** non viene visualizzata nell'elenco di cartelle della visualizzazione albero di Gestione frammenti di codice, seguire questa procedura per aggiungere di nuovo i frammenti per il refactoring in Gestione frammenti di codice.  
  
2.  Scegliere **Gestione frammenti di codice** dal menu **Strumenti**.  
  
3.  Nella finestra di dialogo **Gestione frammenti di codice** selezionare **Visual C#** nell'elenco a discesa **Linguaggio**.  
  
4.  Fare clic su **Aggiungi**. Viene visualizzata la finestra di dialogo **Directory dei frammenti di codice**, che consente di individuare e specificare la directory da aggiungere nuovamente a Gestione frammenti di codice.  
  
5.  Individuare la cartella **Refactoring**, il cui percorso di directory è:  
  
     *Directory di installazione*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID linguaggio*\Refactoring  
  
     Per un'installazione predefinita, il percorso effettivo è simile al seguente:  
  
     C:\Programmi\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6.  Fare clic su **Apri** nella finestra di dialogo **Directory dei frammenti di codice** e quindi su **OK** in Gestione frammenti di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Frammenti di codice Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Frammenti di codice](../ide/code-snippets.md)


