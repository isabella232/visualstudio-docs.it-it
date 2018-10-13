---
title: Barra degli strumenti di Spy + + | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ffc118818bd7af3f79b9c636dc4236ac0031af3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224705"
---
# <a name="spy-toolbar"></a>Barra degli strumenti di Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Barra degli strumenti viene visualizzata sotto la barra del menu Spy + +. Per visualizzare o nascondere la barra degli strumenti, nella **vista** menu, fare clic su **sulla barra degli strumenti**.  
  
 I seguenti controlli sono disponibili sulla barra degli strumenti.  
  
## <a name="uielement-list"></a>Elenco UIElement  
  
|Button|Effetto|  
|------------|------------|  
|![Spy&#43; &#43; pulsante di Windows](../debugger/media/icon-spy-windows.gif "Icon_Spy + + Windows")|Consente di visualizzare una visualizzazione struttura ad albero dei controlli e windows nel sistema. Per altre informazioni, vedere [Windows Vista](../debugger/windows-view.md).|  
|![Spy&#43; &#43; pulsante elabora](../debugger/media/icon-spy-processes.gif "Icon_Spy + + _Processes")|Consente di visualizzare una visualizzazione struttura ad albero dei processi nel sistema. Per altre informazioni, vedere [visualizzazione processi](../debugger/processes-view.md).|  
|![Spy&#43; &#43; pulsante di thread](../debugger/media/icon-spy-threads.gif "Icon_Spy + + _Threads")|Consente di visualizzare una visualizzazione struttura ad albero dei thread del sistema. Per altre informazioni, vedere [visualizzazione thread](../debugger/threads-view.md).|  
|![Spy&#43; &#43; pulsante di messaggi](../debugger/media/icon-spy-messages.gif "Icon_Spy + + messaggi")|Crea una finestra per visualizzare i messaggi della finestra e apre la **Opzioni messaggio** finestra di dialogo in cui è possibile selezionare la finestra di cui i messaggi verranno visualizzati e le altre opzioni. Per altre informazioni, vedere [visualizzazione messaggi](../debugger/messages-view.md).|  
|![Spy&#43; &#43; Log pulsante Avvia](../debugger/media/icon-spy-startlog.gif "Icon_Spy + + _StartLog")|Avvia la registrazione dei messaggi e consente di visualizzare il flusso del messaggio. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva. Per altre informazioni, vedere [procedura: avviare e arrestare la visualizzazione dei Log messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; pulsante Arresta registro](../debugger/media/icon-spy-stoplog.gif "Icon_Spy + + _StopLog")|La registrazione e la visualizzazione del flusso di messaggi dei messaggi viene arrestato. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva. Per altre informazioni, vedere [procedura: avviare e arrestare la visualizzazione dei Log messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; pulsante Opzioni Log](../debugger/media/icon-spy-logoptions.gif "Icon_Spy + + _LogOptions")|Consente di visualizzare il [Opzioni messaggio](../debugger/message-options-dialog-box.md) nella finestra di dialogo. Usare questa finestra di dialogo per selezionare windows e tipi per la visualizzazione di messaggi. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva.|  
|![Spy&#43; &#43; Log pulsante Cancella](../debugger/media/spy-clearlog.gif "Spy + + _ClearLog")|Cancella il contenuto dell'oggetto attivo **messaggi** finestra. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva.|  
|![Spy&#43; &#43; pulsante Trova finestra](../debugger/media/icon-spy-findwindow.gif "Icon_Spy + + _FindWindow")|Apre la [Trova finestra](../debugger/find-window-dialog-box.md) nella finestra di dialogo consente di impostare i criteri di ricerca di finestra e visualizzare le proprietà o i messaggi. Per altre informazioni, vedere [procedura: usare lo strumento di ricerca](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; pulsante Trova prima finestra](../debugger/media/icon-spy-window.gif "Icon_Spy + + _Window")|Consente la visualizzazione corrente per una finestra corrispondente, processo, thread o messaggio.|  
|![Spy&#43; &#43; pulsante Trova finestra successiva](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy + + _NextWindow")|Consente la visualizzazione corrente per la finestra corrispondente successiva, processo, thread o messaggio. Questo controllo (e il comando di menu correlati) è disponibile solo quando è presente un risultato di ricerca valida che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci perché è presente solo una finestra nell'albero della finestra con tale handle; In questo caso **Trova successivo** non è disponibile.|  
|![Spy&#43; &#43; precedente pulsante Trova finestra](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy + + _PrevWindow")|Consente la visualizzazione corrente per la finestra corrispondente precedente, processo, thread o messaggio. Questo controllo (e il comando di menu correlati) è disponibile solo quando è presente un risultato di ricerca valida che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci perché è presente solo una finestra nell'albero della finestra con tale handle; In questo caso **Trova precedente** non è disponibile.|  
|![Spy&#43; &#43; pulsante delle proprietà Explorer](../debugger/media/icon-spy-propexp.gif "Icon_Spy + + _PropExp")|Visualizza le proprietà della finestra che sia selezionata nella visualizzazione di Windows.|  
|![Spy&#43; &#43; pulsante di aggiornamento](../debugger/media/icon-spy-refresh.gif "Icon_Spy + + Aggiorna")|Consente di aggiornare le viste di sistema.|  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di Spy + +](../debugger/using-spy-increment.md)   
 [Visualizzazioni di Spy + +](../debugger/spy-increment-views.md)   
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)



