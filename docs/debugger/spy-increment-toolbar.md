---
title: Barra degli strumenti di Spy + + | Microsoft Docs
description: Informazioni sugli elementi dell'interfaccia utente nella barra degli strumenti di Spy + +, visualizzata sotto la barra dei menu. Per visualizzare o nascondere la barra degli strumenti, scegliere barra degli strumenti dal menu Visualizza.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9dc2564a69c291055d53e358c084e7dd9c4d0506
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148195"
---
# <a name="spy-toolbar"></a>Barra degli strumenti di Spy++
La barra degli strumenti viene visualizzata sotto la barra dei menu in Spy + +. Per visualizzare o nascondere la barra degli strumenti, scegliere **barra degli** strumenti dal menu **Visualizza** .

 Sulla barra degli strumenti sono disponibili i controlli seguenti.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

|Pulsante|Effetto|
|------------|------------|
|![Pulsante Spy&#43;&#43; Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Consente di visualizzare una visualizzazione albero delle finestre e dei controlli presenti nel sistema. Per ulteriori informazioni, vedere [visualizzazione di Windows](../debugger/windows-view.md).|
|![Pulsante di Spy&#43;&#43; processi](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Consente di visualizzare una visualizzazione albero dei processi nel sistema. Per altre informazioni, vedere [visualizzazione processi](../debugger/processes-view.md).|
|![Pulsante spia thread&#43;&#43; ](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Consente di visualizzare una visualizzazione albero dei thread nel sistema. Per altre informazioni, vedere [visualizzazione thread](../debugger/threads-view.md).|
|![Pulsante messaggi Spy&#43;&#43; ](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Consente di creare una finestra per visualizzare i messaggi della finestra e di aprire la finestra di dialogo **Opzioni messaggio** , in modo che sia possibile selezionare la finestra di cui verranno visualizzati i messaggi e selezionare anche altre opzioni. Per altre informazioni, vedere [visualizzazione messaggi](../debugger/messages-view.md).|
|![Spy&#43;&#43; pulsante Avvia log](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Avvia la registrazione dei messaggi e visualizza il flusso di messaggi. Questo controllo è disponibile solo quando una finestra **messaggi** è la finestra attiva. Per ulteriori informazioni, vedere [procedura: avviare e arrestare la visualizzazione del log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Pulsante Stop log di Spy&#43;&#43; ](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Interrompe la registrazione dei messaggi e la visualizzazione del flusso di messaggi. Questo controllo è disponibile solo quando una finestra **messaggi** è la finestra attiva. Per ulteriori informazioni, vedere [procedura: avviare e arrestare la visualizzazione del log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Pulsante Opzioni log di Spy&#43;&#43; ](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Consente di visualizzare la finestra di dialogo [Opzioni messaggio](../debugger/message-options-dialog-box.md) . Utilizzare questa finestra di dialogo per selezionare Windows e i tipi di messaggio per la visualizzazione. Questo controllo è disponibile solo quando una finestra **messaggi** è la finestra attiva.|
|![Pulsante Cancella log di Spy&#43;&#43; ](../debugger/media/spy--_clearlog.gif "_ClearLog di Spy + +")|Cancella il contenuto della finestra **messaggi** attivi. Questo controllo è disponibile solo quando una finestra **messaggi** è la finestra attiva.|
|![Pulsante Trova finestra di Spy&#43;&#43; ](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Apre la [finestra di dialogo Trova finestra](../debugger/find-window-dialog-box.md) , che consente di impostare i criteri di ricerca della finestra e di visualizzare proprietà o messaggi. Per altre informazioni, vedere [procedura: usare lo strumento di ricerca](../debugger/how-to-use-the-finder-tool.md).|
|![Pulsante trova prima finestra di Spy&#43;&#43; ](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Cerca nella visualizzazione corrente una finestra, un processo, un thread o un messaggio corrispondente.|
|![Spy&#43;&#43; trova finestra successiva pulsante](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Cerca nella visualizzazione corrente la finestra, il processo, il thread o il messaggio corrispondente successivo. Questo controllo (e il comando di menu correlato) è disponibile solo se è presente un risultato di ricerca valido che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, viene generato un risultato univoco perché nella struttura ad albero della finestra è presente una sola finestra con tale handle; in questa istanza, **Trova successivo** non è disponibile.|
|![Spy&#43;&#43; trova pulsante della finestra precedente](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Cerca nella visualizzazione corrente la finestra, il processo, il thread o il messaggio corrispondente precedente. Questo controllo (e il comando di menu correlato) è disponibile solo se è presente un risultato di ricerca valido che non è univoco. Ad esempio, quando si usa un handle di finestra come criterio di ricerca nell'albero della finestra, viene generato un risultato univoco perché nella struttura ad albero della finestra è presente una sola finestra con tale handle; in questo caso, **Trova precedente** non è disponibile.|
|![Pulsante Esplora proprietà di Spy&#43;&#43; ](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Consente di visualizzare le proprietà della finestra selezionata nella visualizzazione Windows.|
|![Pulsante di aggiornamento Spy&#43;&#43; ](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Aggiorna le visualizzazioni di sistema.|

## <a name="see-also"></a>Vedere anche
- [Utilizzo di Spy++](../debugger/using-spy-increment.md)
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [Riferimenti per Spy++](../debugger/spy-increment-reference.md)