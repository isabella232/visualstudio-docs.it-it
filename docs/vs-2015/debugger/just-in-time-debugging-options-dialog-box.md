---
title: Just-In-Time, debug, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5522c9da025b76a3892d3923cdd7397b8ed5ce5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207493"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>JIT, Debug, Finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per l'accesso il **Just-In-Time** page, passare al **strumenti** dal menu **opzioni**. Nel **opzioni** finestra di dialogo espandere il **Debugging** nodo e selezionare **Just-In-Time**. Questa pagina consente di abilitare il debug JIT per codice gestito, codice nativo e script. Per altre informazioni, vedere [debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 È possibile abilitare il debug JIT per questi tipi di programma:  
  
-   Gestito  
  
-   Nativo  
  
-   Script  
  
 Il debug JIT è una tecnica per il debug di un programma avviato al di fuori di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. È possibile eseguire un programma creato in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] al di fuori dell'ambiente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Se il debug JIT è abilitato e si verifica un arresto anomalo, viene visualizzata una finestra di dialogo in cui viene chiesto se si desidera eseguire il debug.  
  
## <a name="associated-warnings"></a>Avvisi associati  
 Quando si visita questa pagina della finestra di **opzioni** nella finestra di dialogo si potrebbe essere visualizzato un messaggio simile al seguente:  
  
 **Un altro debugger è registrata come Just-In-Time debugger. Per correggere, abilitare Just-In-Time di debug o ripristinare Visual Studio.**  
  
 Questo messaggio viene visualizzato se come debugger JIT è impostato un altro debugger, ad esempio una versione precedente del debugger di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 È anche possibile che venga visualizzato il messaggio seguente:  
  
 **Just-In-Time debug rilevati errori di registrazione. Per correggere, abilitare Just-In-Time di debug o ripristinare Visual Studio.**  
  
 Se viene visualizzato uno di questi avvisi, eseguire il debug con Just-In-Time [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] richiede privilegi di amministratore fino a quando non è stato risolto il problema. Se si tenta di abilitare la modalità JIT in queste condizioni senza disporre di questi privilegi, viene visualizzato il seguente messaggio di errore:  
  
 **Accesso negato. Dispone un amministratore enable Just-In-Time di debug o ripristinare l'installazione di Visual Studio.**  
  
## <a name="see-also"></a>Vedere anche  
 [Il debug, finestra di dialogo Opzioni](../debugger/debugging-options-dialog-box.md)   
 [Procedura: Specificare le impostazioni del debugger](../debugger/how-to-specify-debugger-settings.md)



