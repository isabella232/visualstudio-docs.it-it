---
title: Finestra di dialogo Proprietà messaggio | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62846115"
---
# <a name="message-properties-dialog-box"></a>Finestra di dialogo Proprietà messaggio
Utilizzare questa finestra di dialogo per ottenere ulteriori informazioni su un messaggio specifico. Per visualizzare questa finestra di dialogo, spostare lo stato attivo in una finestra [visualizzazione messaggi](../debugger/messages-view.md) . Selezionare un nodo del messaggio nell'albero, quindi scegliere **Proprietà** dal menu **Visualizza** .

 La scheda **generale** è l'unica scheda visualizzata. Sono disponibili le impostazioni seguenti:

 **Handle finestra** ID univoco di questa finestra. I numeri di handle della finestra vengono riutilizzati. identificano una finestra solo per la durata di tale finestra. Fare clic su questo valore per visualizzare le proprietà di questa finestra.

 **Livello di annidamento** Profondità di annidamento di questo messaggio, dove 0 non è annidamento.

 **Messaggio** di Numero, stato e nome del messaggio di Windows selezionato.

 **LRESULT** Valore del parametro *LRESULT* , se disponibile.

 **wParam** Valore del parametro *wParam* , se disponibile.

 **lParam** Valore del parametro *lParam* , se disponibile. Questo valore viene decodificato se è un puntatore a una stringa o a una struttura.

## <a name="related-sections"></a>Sezioni correlate
 Finestra di [dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) Consente di selezionare i messaggi elencati nella visualizzazione messaggi attivi.

 Finestra di [dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md) Utilizzato per trovare il nodo di un messaggio specifico nella visualizzazione messaggi.

 [Riferimenti per Spy + +](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy + +.

 [Apertura della visualizzazione messaggi dalla finestra trova](../debugger/how-to-open-messages-view-from-find-window.md) Viene illustrato come aprire la visualizzazione messaggi dalla finestra di dialogo Trova finestra.

 [Ricerca di un messaggio nella visualizzazione messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md) Viene illustrato come trovare un messaggio specifico nella visualizzazione messaggi.

 [Visualizzazione messaggi](../debugger/messages-view.md) Consente di visualizzare il flusso di messaggi associato a una finestra, un processo o un thread.

 [Viste di Spy + +](../debugger/spy-increment-views.md) Illustra le visualizzazioni ad albero di Spy + + di Windows, i messaggi, i processi e i thread.

 [Uso di Spy + +](../debugger/using-spy-increment.md) Introduce lo strumento Spy + + e spiega come può essere usato.