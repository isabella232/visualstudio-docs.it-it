---
title: Visualizzazione messaggi | Microsoft Docs
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
ms.openlocfilehash: 6b20ed28518c9156e82c6fe75ecceda74c66615d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62845852"
---
# <a name="messages-view"></a>Visualizzazione messaggi
A ogni finestra è associato un flusso di messaggi. In una finestra di visualizzazione messaggi viene visualizzato questo flusso di messaggi. Vengono visualizzati l'handle della finestra, il codice del messaggio e il messaggio. È possibile creare una visualizzazione messaggi anche per un thread o un processo. In questo modo è possibile visualizzare i messaggi inviati a tutte le finestre di proprietà di un processo o thread specifico, che risulta particolarmente utile per l'acquisizione dei messaggi di inizializzazione della finestra.

 Di seguito viene visualizzata una finestra di visualizzazione dei messaggi tipica. Si noti che la prima colonna contiene l'handle di finestra e la seconda colonna contiene un codice di messaggio (descritto in [codici messaggi](../debugger/message-codes.md)). I parametri e i valori restituiti dei messaggi decodificati sono a destra.

 ![Visualizzazione messaggi di Spy&#43;&#43; ](../debugger/media/spy--_messagesview.png "_MessagesView di Spy + +") Visualizzazione messaggi di Spy + +

## <a name="procedures"></a>Procedure

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Per aprire una visualizzazione messaggi per una finestra, un processo o un thread

1. Spostare lo stato attivo in una [visualizzazione di Windows](../debugger/windows-view.md), nella [visualizzazione processi](../debugger/processes-view.md)o nella finestra [visualizzazione thread](../debugger/threads-view.md) .

2. Individuare il nodo per l'elemento di cui si desidera esaminare i messaggi e selezionarlo.

3. Dal menu **Spy** scegliere **log messages**.

     Verrà visualizzata la finestra di [dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) .

4. Selezionare le opzioni per il messaggio che si desidera visualizzare.

5. Premere **OK** per avviare la registrazione dei messaggi.

     Viene visualizzata una finestra Visualizzazione messaggi e viene aggiunto un menu **messaggi** alla barra degli strumenti di Spy + +. A seconda delle opzioni selezionate, i messaggi iniziano a trasmettere nella finestra Visualizzazione messaggi attivi.

6. Quando si dispone di un numero sufficiente di messaggi, scegliere **Interrompi registrazione** dal menu **messaggi** .

## <a name="in-this-section"></a>Contenuto della sezione
 [Controllo della visualizzazione dei messaggi](../debugger/how-to-control-messages-view.md) Viene illustrato come gestire la visualizzazione dei messaggi.

 [Apertura della visualizzazione messaggi dalla finestra trova](../debugger/how-to-open-messages-view-from-find-window.md) Viene illustrato come aprire la visualizzazione messaggi dalla finestra di dialogo Trova finestra.

 [Ricerca di un messaggio nella visualizzazione messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md) Viene illustrato come trovare un messaggio specifico nella visualizzazione messaggi.

 [Avvio e arresto della visualizzazione del log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md) Viene illustrato come avviare e arrestare la registrazione di messaggi.

 [Codici di messaggio](../debugger/message-codes.md) Definisce i codici per i messaggi elencati nella visualizzazione messaggi.

 [Visualizzazione delle proprietà del messaggio](../debugger/how-to-display-message-properties.md) Come visualizzare ulteriori informazioni su un messaggio.

## <a name="related-sections"></a>Sezioni correlate
 [Viste di Spy + +](../debugger/spy-increment-views.md) Illustra le visualizzazioni ad albero di Spy + + di Windows, i messaggi, i processi e i thread.

 [Uso di Spy + +](../debugger/using-spy-increment.md) Introduce lo strumento Spy + + e spiega come può essere usato.

 Finestra di [dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) Consente di selezionare i messaggi elencati nella visualizzazione messaggi attivi.

 Finestra di [dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md) Utilizzato per trovare il nodo di un messaggio specifico nella visualizzazione messaggi.

 Finestra di [dialogo Proprietà messaggio](../debugger/message-properties-dialog-box.md) Utilizzato per visualizzare le proprietà di un messaggio selezionato in visualizzazione messaggio.

 [Riferimenti per Spy + +](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy + +.