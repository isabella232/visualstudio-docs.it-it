---
title: Barra degli strumenti di Spy + + | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7a3213d614caa19fb6df77a72efd05e36484c77
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982676"
---
# <a name="spy-toolbar"></a>Barra degli strumenti di Spy++
Barra degli strumenti viene visualizzata sotto la barra del menu Spy + +. Per visualizzare o nascondere la barra degli strumenti, nella **vista** menu, fare clic su **sulla barra degli strumenti**.  
  
 I seguenti controlli sono disponibili sulla barra degli strumenti.  
  
## <a name="uielement-list"></a>Elenco UIElement  
  
|Button|Effetto|  
|------------|------------|  
|![Spy&#43; &#43; pulsante di Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + Windows")|Consente di visualizzare una visualizzazione struttura ad albero dei controlli e windows nel sistema. Per altre informazioni, vedere [Windows Vista](../debugger/windows-view.md).|  
|![Spy&#43; &#43; pulsante elabora](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Consente di visualizzare una visualizzazione struttura ad albero dei processi nel sistema. Per altre informazioni, vedere [visualizzazione processi](../debugger/processes-view.md).|  
|![Spy&#43;&#43; pulsante Thread](../debugger/media/icon_spy--_threads.gif "Icon_Spy++_Threads")|Consente di visualizzare una visualizzazione struttura ad albero dei thread del sistema. Per altre informazioni, vedere [visualizzazione thread](../debugger/threads-view.md).|  
|![Spy&#43; &#43; pulsante di messaggi](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + messaggi")|Crea una finestra per visualizzare i messaggi della finestra e apre la **Opzioni messaggio** finestra di dialogo in cui è possibile selezionare la finestra di cui i messaggi verranno visualizzati e le altre opzioni. Per altre informazioni, vedere [visualizzazione messaggi](../debugger/messages-view.md).|  
|![Spy&#43; &#43; Log pulsante Avvia](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Avvia la registrazione dei messaggi e consente di visualizzare il flusso del messaggio. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva. Per altre informazioni, vedere [procedura: avviare e arrestare la visualizzazione dei Log messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43;&#43; pulsante Arresta registro](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy++_StopLog")|La registrazione e la visualizzazione del flusso di messaggi dei messaggi viene arrestato. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva. Per altre informazioni, vedere [procedura: avviare e arrestare la visualizzazione dei Log messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; pulsante Opzioni Log](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Consente di visualizzare il [Opzioni messaggio](../debugger/message-options-dialog-box.md) nella finestra di dialogo. Usare questa finestra di dialogo per selezionare windows e tipi per la visualizzazione di messaggi. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva.|  
|![Spy&#43; &#43; Log pulsante Cancella](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|Cancella il contenuto dell'oggetto attivo **messaggi** finestra. Questo controllo è disponibile solo quando un **messaggi** finestra è la finestra attiva.|  
|![Spy&#43; &#43; pulsante Trova finestra](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Apre la [Trova finestra](../debugger/find-window-dialog-box.md) nella finestra di dialogo consente di impostare i criteri di ricerca di finestra e visualizzare le proprietà o i messaggi. Per altre informazioni, vedere [procedura: usare lo strumento di ricerca](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; pulsante Trova prima finestra](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Consente la visualizzazione corrente per una finestra corrispondente, processo, thread o messaggio.|  
|![Spy&#43; &#43; pulsante Trova finestra successiva](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Consente la visualizzazione corrente per la finestra corrispondente successiva, processo, thread o messaggio. Questo controllo (e il comando di menu correlati) è disponibile solo quando è presente un risultato di ricerca valida che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci perché è presente solo una finestra nell'albero della finestra con tale handle; In questo caso **Trova successivo** non è disponibile.|  
|![Spy&#43; &#43; precedente pulsante Trova finestra](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Consente la visualizzazione corrente per la finestra corrispondente precedente, processo, thread o messaggio. Questo controllo (e il comando di menu correlati) è disponibile solo quando è presente un risultato di ricerca valida che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci perché è presente solo una finestra nell'albero della finestra con tale handle; In questo caso **Trova precedente** non è disponibile.|  
|![Spy&#43; &#43; pulsante delle proprietà Explorer](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Visualizza le proprietà della finestra che sia selezionata nella visualizzazione di Windows.|  
|![Spy&#43; &#43; pulsante di aggiornamento](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + Aggiorna")|Consente di aggiornare le viste di sistema.|  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Spy++](../debugger/using-spy-increment.md)   
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)   
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)