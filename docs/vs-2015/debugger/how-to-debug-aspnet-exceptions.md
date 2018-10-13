---
title: 'Procedura: eseguire il Debug di eccezioni ASP.NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a08e382ed9d97aa659012934d3edef45151e10ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178529"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Procedura: debug di eccezioni ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debug delle eccezioni è una parte importante dello sviluppo di un solido [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dell'applicazione. Informazioni generali su come eseguire il debug di eccezioni, vedere [la gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Per eseguire il debug non gestite [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] eccezioni, è necessario assicurarsi che il debugger si arresta per loro. Il runtime di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dispone di un gestore eccezioni di livello superiore. Di conseguenza, per impostazione predefinita il debugger non si interrompe mai in corrispondenza di eccezioni non gestite. Per interrompere il debugger quando viene generata un'eccezione, è necessario selezionare **Interrompi quando un'eccezione è: generata** impostazione per tale eccezione nella **eccezioni** nella finestra di dialogo.  
  
 Se è stato abilitato Just My Code **Interrompi quando un'eccezione è: generata** non causa il debugger per interrompere immediatamente se viene generata un'eccezione in un metodo .NET Framework o altro codice di sistema. Invece l'esecuzione continua sino al raggiungimento di codice non di sistema, quindi si interrompe. Non è pertanto necessario eseguire il codice di sistema quando si verifica un'eccezione.  
  
 Just My Code fornisce un'altra opzione che può rivelarsi molto utile: **Interrompi quando un'eccezione è: User-unhandled**. Se si sceglie questa impostazione per un'eccezione, il debugger interromperà l'esecuzione nel codice utente, ma solo se l'eccezione non viene intercettata e gestita dal codice utente. Questa impostazione annulla l'effetto del gestore eccezioni di primo livello di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], perché quest'ultimo si trova nel codice non utente.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Per attivare il debug delle eccezioni ASP.NET con Just My Code  
  
1.  Nel **Debug** menu, fare clic su **eccezioni**.  
  
     Il **eccezioni** verrà visualizzata la finestra di dialogo.  
  
2.  Nel **eccezioni Common Language Runtime** riga, seleziona **generata** oppure **User-unhandled**.  
  
     Usare la **User-unhandled** impostato, **Just My Code** deve essere abilitata...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Procedure ottimali per la gestione delle eccezioni ASP.NET  
  
-   Collocare blocchi `try … catch` attorno al codice che può generare eccezioni anticipabili e gestibili. Ad esempio, se l'applicazione effettua chiamate a un servizio Web XML o direttamente a un Server SQL, il codice dovrebbe trovarsi nel **try... catch** blocca perché vi sono numerose eccezioni che possono verificarsi.



