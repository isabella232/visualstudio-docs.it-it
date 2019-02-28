---
title: Finestra di dialogo proprietà del messaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f590f40e4e3361f4dbeb46a3a9b8758b8ab5075
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705372"
---
# <a name="message-properties-dialog-box"></a>Finestra di dialogo Proprietà messaggio
Usare questa finestra di dialogo per altre informazioni su un determinato messaggio. Per visualizzare questa finestra di dialogo, spostare lo stato attivo a un [visualizzazione messaggi](../debugger/messages-view.md) finestra. Selezionare qualsiasi nodo di messaggio nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.

 Il **generale** scheda è l'unico visualizzato. Sono disponibili le seguenti impostazioni:

 **Handle di finestra** l'ID univoco di questa finestra. I numeri degli handle di finestra vengono riutilizzati; una finestra consentono di identificare solo per la durata di tale finestra. Fare clic su questo valore per visualizzare le proprietà di questa finestra.

 **Livello di nidificazione** profondità di annidamento di questo messaggio, dove 0 non è alcun annidamento.

 **Messaggio** numero, stato e nome del messaggio windows selezionati.

 **lResult** il valore della *lResult* parametro, se presente.

 **wParam** il valore della *wParam* parametro, se presente.

 **lParam** il valore della *lParam* parametro, se presente. Se è un puntatore a una stringa o una struttura, questo valore è decodificato.

## <a name="related-sections"></a>Sezioni correlate
 [Finestra di dialogo Opzioni del messaggio](../debugger/message-options-dialog-box.md) utilizzato per selezionare quali messaggi sono elencati nella visualizzazione messaggi attiva.

 [Finestra di dialogo di ricerca del messaggio](../debugger/message-search-dialog-box.md) consente di individuare il nodo di un messaggio specifico nella visualizzazione dei messaggi.

 [Riferimenti per Spy + +](../debugger/spy-increment-reference.md) include sezioni che descrivono ogni Spy + + menu e la finestra di dialogo.

 [Apertura della visualizzazione messaggi dalla finestra Trova](../debugger/how-to-open-messages-view-from-find-window.md) viene illustrato come aprire la visualizzazione messaggi dalla finestra di dialogo Trova finestra.

 [La ricerca di un messaggio in messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md) viene spiegato come individuare un messaggio specifico nella visualizzazione dei messaggi.

 [La visualizzazione messaggi](../debugger/messages-view.md) consente di visualizzare il flusso del messaggio associato a una finestra, processo o thread.

 [Visualizzazioni di Spy + +](../debugger/spy-increment-views.md) spiega le visualizzazioni dell'albero Spy + + di windows, i messaggi, processi e thread.

 [Utilizzo di Spy + +](../debugger/using-spy-increment.md) introduce lo strumento Spy + + e spiega come può essere usato.