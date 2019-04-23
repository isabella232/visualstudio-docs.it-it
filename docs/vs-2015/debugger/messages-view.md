---
title: La visualizzazione messaggi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3765b9804224549c98b57cd1b0a44f0330d278b5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080579"
---
# <a name="messages-view"></a>Visualizzazione messaggi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ogni finestra dispone di un flusso di messaggi associati. Questo flusso di messaggi viene visualizzata una finestra di visualizzazione dei messaggi. L'handle di finestra, codice di messaggio e il messaggio vengono visualizzati. È possibile creare una visualizzazione di messaggi per un thread o processo anche. In questo modo è possibile visualizzare i messaggi inviati a tutte le finestre appartenenti a un determinato processo o thread, che risulta particolarmente utile per l'acquisizione di messaggi di inizializzazione della finestra.  
  
 Di seguito è riportata una finestra di visualizzazione di messaggi tipici. Si noti che la prima colonna contiene l'handle della finestra e la seconda colonna contiene un codice del messaggio (illustrato in [codici di messaggio](../debugger/message-codes.md)). Messaggio decodificato parametri e valori restituiti sono sul lato destro.  
  
 ![Spy&#43; &#43; la visualizzazione messaggi](../debugger/media/spy-messagesview.png "Spy + + _MessagesView")  
Visualizzazione messaggi di Spy++  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Per aprire una visualizzazione di messaggi per una finestra, processo o thread  
  
1. Spostare lo stato attivo a un [Windows Vista](../debugger/windows-view.md), [visualizzazione processi](../debugger/processes-view.md), o [visualizzazione thread](../debugger/threads-view.md) finestra.  
  
2. Trovare il nodo per l'elemento di cui si desidera esaminare i messaggi e selezionarlo.  
  
3. Dal **Spy** menu, scegliere **i messaggi di Log**.  
  
     Il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) apre.  
  
4. Selezionare le opzioni per il messaggio da visualizzare.  
  
5. Premere **OK** per avviare la registrazione messaggi.  
  
     Un viene visualizzata la finestra di visualizzazione dei messaggi e un **messaggi** menu viene aggiunto alla barra degli strumenti di Spy + +. A seconda delle opzioni selezionate, i messaggi di avviare lo streaming nella finestra di visualizzazione di messaggi attiva.  
  
6. Quando si dispone di messaggi sufficiente, scegliere **Arresta registrazione** dalle **messaggi** menu.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Controllo della visualizzazione messaggi](../debugger/how-to-control-messages-view.md)  
 Viene illustrato come gestire la visualizzazione dei messaggi.  
  
 [La ricerca di un messaggio nella visualizzazione messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Viene illustrato come individuare un messaggio specifico nella visualizzazione dei messaggi.  
  
 [Avviare e arrestare la visualizzazione del Log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Viene illustrato come avviare e arrestare la registrazione dei messaggi.  
  
 [Codici di messaggio](../debugger/message-codes.md)  
 Definisce i codici per i messaggi elencati nella visualizzazione dei messaggi.  
  
 [Visualizzazione delle proprietà di messaggio](../debugger/how-to-display-message-properties.md)  
 Come visualizzare altre informazioni su un messaggio.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)  
 Illustra le visualizzazioni dell'albero Spy + + di windows, i messaggi, processi e thread.  
  
 [Uso di Spy++](../debugger/using-spy-increment.md)  
 Introduce lo strumento Spy + + e spiega come può essere usato.  
  
 [Finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md)  
 Consente di selezionare quali messaggi sono elencati nella visualizzazione messaggi attiva.  
  
 [Finestra di dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md)  
 Utilizzato per trovare il nodo di un messaggio specifico nella visualizzazione dei messaggi.  
  
 [Finestra di dialogo Proprietà messaggio](../debugger/message-properties-dialog-box.md)  
 Consente di visualizzare le proprietà di un messaggio selezionato nella visualizzazione di messaggi.  
  
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)  
 Include varie sezioni che descrivono ogni Spy + + menu e la finestra di dialogo.
