---
title: Barra degli strumenti di Spy++ | Microsoft Docs
description: Comprendere gli elementi dell'interfaccia utente nella barra degli strumenti di Spy++, visualizzata sotto la barra dei menu. Per visualizzare o nascondere la barra degli strumenti, scegliere Barra degli strumenti dal menu Visualizza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 97c03fe68b810cbd7e907b4020b8487ae5c547f2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636587"
---
# <a name="spy-toolbar"></a>Barra degli strumenti di Spy++
La barra degli strumenti viene visualizzata sotto la barra dei menu in Spy++. Per visualizzare o nascondere la barra degli strumenti, **scegliere** Barra degli strumenti dal menu **Visualizza**.

 Sulla barra degli strumenti sono disponibili i controlli seguenti.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

|Button|Effetto|
|------------|------------|
|![Pulsante&#43;&#43; Windows Spy](../debugger/media/icon_spy--_windows.gif "Icon_Spy++_Windows")|Visualizza una visualizzazione albero delle finestre e dei controlli nel sistema. Per altre informazioni, vedere [Windows View](../debugger/windows-view.md).|
|![Pulsante Processi&#43;&#43; Spy](../debugger/media/icon_spy--_processes.gif "Icon_Spy++_Processes")|Visualizza una visualizzazione albero dei processi nel sistema. Per altre informazioni, vedere [Visualizzazione Processi.](../debugger/processes-view.md)|
|![Pulsante Thread&#43;&#43; Spy](../debugger/media/icon_spy--_threads.gif "Icon_Spy++_Threads")|Visualizza una visualizzazione albero dei thread nel sistema. Per altre informazioni, vedere [Visualizzazione Thread.](../debugger/threads-view.md)|
|![Pulsante Messaggi&#43;&#43; Spy](../debugger/media/icon_spy--_messages.gif "Icon_Spy++_Messages")|Crea una finestra per visualizzare i messaggi della finestra e apre la finestra di dialogo **Opzioni** messaggio in modo che sia possibile selezionare la finestra i cui messaggi verranno visualizzati e selezionare anche altre opzioni. Per altre informazioni, vedere [Visualizzazione Messaggi.](../debugger/messages-view.md)|
|![Pulsante Start Log (Avvia log) di Spy&#43;&#43; ](../debugger/media/icon_spy--_startlog.gif "Icon_Spy++_StartLog")|Avvia la registrazione dei messaggi e visualizza il flusso dei messaggi. Questo controllo è disponibile solo quando **una finestra** Messaggi è la finestra attiva. Per altre informazioni, vedere [Procedura: Avviare e arrestare la visualizzazione del log dei messaggi.](../debugger/how-to-start-and-stop-the-message-log-display.md)|
|![Pulsante Arresta log di Spy&#43;&#43; ](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy++_StopLog")|Arresta la registrazione dei messaggi e la visualizzazione del flusso di messaggi. Questo controllo è disponibile solo quando **una finestra** Messaggi è la finestra attiva. Per altre informazioni, vedere [Procedura: Avviare e arrestare la visualizzazione del log dei messaggi.](../debugger/how-to-start-and-stop-the-message-log-display.md)|
|![Pulsante opzioni log&#43;&#43; Spy](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy++_LogOptions")|Consente di visualizzare [la finestra di dialogo](../debugger/message-options-dialog-box.md) Opzioni messaggio . Utilizzare questa finestra di dialogo per selezionare le finestre e i tipi di messaggio da visualizzare. Questo controllo è disponibile solo quando **una finestra** Messaggi è la finestra attiva.|
|![Pulsante&#43;&#43; Cancella log di Spy](../debugger/media/spy--_clearlog.gif "Spy++_ClearLog")|Cancella il contenuto della finestra **Messaggi** attiva. Questo controllo è disponibile solo quando **una finestra** Messaggi è la finestra attiva.|
|![Pulsante&#43;&#43; Trova finestra di Spy](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy++_FindWindow")|Apre la [finestra di dialogo Trova](../debugger/find-window-dialog-box.md) finestra che consente di impostare i criteri di ricerca della finestra e visualizzare proprietà o messaggi. Per altre informazioni, vedere [Procedura: Usare lo strumento Finder.](../debugger/how-to-use-the-finder-tool.md)|
|![Spy&#43;&#43; pulsante Trova prima finestra](../debugger/media/icon_spy--_window.gif "Icon_Spy++_Window")|Cerca nella visualizzazione corrente una finestra, un processo, un thread o un messaggio corrispondente.|
|![Pulsante&#43;&#43; Trova finestra successiva di Spy](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy++_NextWindow")|Cerca nella visualizzazione corrente la finestra, il processo, il thread o il messaggio corrispondente successivo. Questo controllo (e il comando di menu correlato) è disponibile solo quando è presente un risultato di ricerca valido non univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci perché nell'albero della finestra è presente una sola finestra con tale handle. In questo caso, **Trova successivo** non è disponibile.|
|![Pulsante&#43;&#43; Trova finestra precedente di Spy](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy++_PrevWindow")|Cerca nella visualizzazione corrente la finestra, il processo, il thread o il messaggio corrispondente precedente. Questo controllo (e il comando di menu correlato) è disponibile solo quando è presente un risultato di ricerca valido non univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, produce risultati univoci perché nell'albero della finestra è presente una sola finestra con tale handle. In questo caso, **Trova precedente** non è disponibile.|
|![Pulsante Esplora&#43;&#43; Spy](../debugger/media/icon_spy--_propexp.gif "Icon_Spy++_PropExp")|Consente di visualizzare le proprietà della finestra selezionata nella Windows visualizzazione.|
|![Pulsante aggiorna&#43;&#43; Spy](../debugger/media/icon_spy--_refresh.gif "Icon_Spy++_Refresh")|Aggiorna le viste di sistema.|

## <a name="see-also"></a>Vedi anche
- [Utilizzo di Spy++](../debugger/using-spy-increment.md)
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [Riferimenti per Spy++](../debugger/spy-increment-reference.md)