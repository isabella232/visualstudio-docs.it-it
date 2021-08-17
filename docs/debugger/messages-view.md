---
title: Visualizzazione messaggi | Microsoft Docs
description: A ogni finestra, thread e processo è associato un flusso di messaggi che può essere visualizzato in una finestra visualizzazione messaggi. Informazioni su come aprire e controllare una visualizzazione messaggi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 858620450452080dbbdf6c9aa5da8ed7c44c13e2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065410"
---
# <a name="messages-view"></a>Visualizzazione messaggi
A ogni finestra è associato un flusso di messaggi. Questo flusso di messaggi viene visualizzato in una finestra di visualizzazione Messaggi. Vengono visualizzati l'handle della finestra, il codice del messaggio e il messaggio. È anche possibile creare una visualizzazione Messaggi per un thread o un processo. In questo modo è possibile visualizzare i messaggi inviati a tutte le finestre di proprietà di un processo o thread specifico, particolarmente utile per l'acquisizione dei messaggi di inizializzazione della finestra.

 Di seguito viene visualizzata una tipica finestra di visualizzazione Messaggi. Si noti che la prima colonna contiene l'handle della finestra e la seconda colonna contiene un codice messaggio (illustrato in [Codici messaggio](../debugger/message-codes.md)). I parametri del messaggio decodificato e i valori restituiti sono a destra.

 ![Visualizzazione messaggi&#43;&#43; Spy](../debugger/media/spy--_messagesview.png "Spy++_MessagesView") Visualizzazione messaggi di Spy++

## <a name="procedures"></a>Procedure

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Per aprire una visualizzazione Messaggi per una finestra, un processo o un thread

1. Spostare lo stato attivo su [una Windows,](../debugger/windows-view.md) [visualizzazione Processi](../debugger/processes-view.md)o [Visualizzazione](../debugger/threads-view.md) thread.

2. Trovare il nodo per l'elemento di cui si vogliono esaminare i messaggi e selezionarlo.

3. Scegliere Log Messages **(Registra messaggi) dal** menu **Spy.**

     Verrà [visualizzata la finestra di dialogo Opzioni](../debugger/message-options-dialog-box.md) messaggio .

4. Selezionare le opzioni per il messaggio che si desidera visualizzare.

5. Premere **OK per** avviare la registrazione dei messaggi.

     Viene visualizzata una finestra di visualizzazione Messaggi e viene **aggiunto un** menu Messaggi alla barra degli strumenti di Spy++. A seconda delle opzioni selezionate, i messaggi iniziano a trasmettere nella finestra di visualizzazione Messaggi attiva.

6. Quando i messaggi sono sufficienti, scegliere **Arresta** registrazione **dal** menu Messaggi.

## <a name="in-this-section"></a>Contenuto della sezione
 [Controllo della visualizzazione messaggi](../debugger/how-to-control-messages-view.md) Viene illustrato come gestire la visualizzazione Messaggi.

 [Apertura della visualizzazione messaggi dalla finestra Trova](../debugger/how-to-open-messages-view-from-find-window.md) Viene illustrato come aprire la visualizzazione Messaggi dalla finestra di dialogo Trova finestra.

 [Ricerca di un messaggio nella visualizzazione messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md) Viene illustrato come trovare un messaggio specifico nella visualizzazione Messaggi.

 [Avvio e arresto della visualizzazione del log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md) Viene illustrato come avviare e arrestare la registrazione dei messaggi.

 [Codici di messaggio](../debugger/message-codes.md) Definisce i codici per i messaggi elencati nella visualizzazione Messaggi.

 [Visualizzazione delle proprietà dei messaggi](../debugger/how-to-display-message-properties.md) Come visualizzare altre informazioni su un messaggio.

## <a name="related-sections"></a>Sezioni correlate
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md) Illustra le visualizzazioni albero di Spy++ di finestre, messaggi, processi e thread.

 [Uso di Spy++](../debugger/using-spy-increment.md) Introduce lo strumento Spy++ e spiega come può essere usato.

 [Finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) Consente di selezionare i messaggi elencati nella visualizzazione Messaggi attiva.

 [Finestra di dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md) Usato per trovare il nodo per un messaggio specifico nella visualizzazione Messaggi.

 [Finestra di dialogo Proprietà messaggio](../debugger/message-properties-dialog-box.md) Consente di visualizzare le proprietà di un messaggio selezionato nella visualizzazione Messaggio.

 [Informazioni di riferimento su Spy++](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy++.