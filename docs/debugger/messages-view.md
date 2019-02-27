---
title: La visualizzazione messaggi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db9d64119a94e2358a6f52e6e1269fca8d726cbb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694400"
---
# <a name="messages-view"></a>Visualizzazione messaggi
Ogni finestra dispone di un flusso di messaggi associati. Questo flusso di messaggi viene visualizzata una finestra di visualizzazione dei messaggi. L'handle di finestra, codice di messaggio e il messaggio vengono visualizzati. È possibile creare una visualizzazione di messaggi per un thread o processo anche. In questo modo è possibile visualizzare i messaggi inviati a tutte le finestre appartenenti a un determinato processo o thread, che risulta particolarmente utile per l'acquisizione di messaggi di inizializzazione della finestra.

 Di seguito è riportata una finestra di visualizzazione di messaggi tipici. Si noti che la prima colonna contiene l'handle della finestra e la seconda colonna contiene un codice del messaggio (illustrato in [codici di messaggio](../debugger/message-codes.md)). Messaggio decodificato parametri e valori restituiti sono sul lato destro.

 ![Spy&#43; &#43; la visualizzazione messaggi](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView") visualizzazione messaggi di Spy + +

## <a name="procedures"></a>Procedure

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Per aprire una visualizzazione di messaggi per una finestra, processo o thread

1.  Spostare lo stato attivo a un [Windows Vista](../debugger/windows-view.md), [visualizzazione processi](../debugger/processes-view.md), o [visualizzazione thread](../debugger/threads-view.md) finestra.

2.  Trovare il nodo per l'elemento di cui si desidera esaminare i messaggi e selezionarlo.

3.  Dal **Spy** menu, scegliere **i messaggi di Log**.

     Il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) apre.

4.  Selezionare le opzioni per il messaggio da visualizzare.

5.  Premere **OK** per avviare la registrazione messaggi.

     Un viene visualizzata la finestra di visualizzazione dei messaggi e un **messaggi** menu viene aggiunto alla barra degli strumenti di Spy + +. A seconda delle opzioni selezionate, i messaggi di avviare lo streaming nella finestra di visualizzazione di messaggi attiva.

6.  Quando si dispone di messaggi sufficiente, scegliere **Arresta registrazione** dalle **messaggi** menu.

## <a name="in-this-section"></a>In questa sezione
 [Controllo della visualizzazione messaggi](../debugger/how-to-control-messages-view.md) spiega come gestire la visualizzazione dei messaggi.

 [Apertura della visualizzazione messaggi dalla finestra Trova](../debugger/how-to-open-messages-view-from-find-window.md) viene illustrato come aprire la visualizzazione messaggi dalla finestra di dialogo Trova finestra.

 [La ricerca di un messaggio in messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md) viene spiegato come individuare un messaggio specifico nella visualizzazione dei messaggi.

 [Avviare e arrestare la visualizzazione dei Log messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md) viene spiegato come avviare e arrestare la registrazione dei messaggi.

 [I codici di messaggio](../debugger/message-codes.md) definisce i codici per i messaggi elencati nella visualizzazione dei messaggi.

 [Visualizzazione delle proprietà di messaggio](../debugger/how-to-display-message-properties.md) come visualizzare ulteriori informazioni su un messaggio.

## <a name="related-sections"></a>Sezioni correlate
 [Visualizzazioni di Spy + +](../debugger/spy-increment-views.md) spiega le visualizzazioni dell'albero Spy + + di windows, i messaggi, processi e thread.

 [Utilizzo di Spy + +](../debugger/using-spy-increment.md) introduce lo strumento Spy + + e spiega come può essere usato.

 [Finestra di dialogo Opzioni del messaggio](../debugger/message-options-dialog-box.md) utilizzato per selezionare quali messaggi sono elencati nella visualizzazione messaggi attiva.

 [Finestra di dialogo di ricerca del messaggio](../debugger/message-search-dialog-box.md) consente di individuare il nodo di un messaggio specifico nella visualizzazione dei messaggi.

 [Finestra di dialogo proprietà del messaggio](../debugger/message-properties-dialog-box.md) consente di visualizzare le proprietà di un messaggio selezionato nella visualizzazione di messaggi.

 [Riferimenti per Spy + +](../debugger/spy-increment-reference.md) include sezioni che descrivono ogni Spy + + menu e la finestra di dialogo.