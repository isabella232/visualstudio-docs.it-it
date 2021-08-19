---
title: Finestra di dialogo Proprietà messaggio | Microsoft Docs
description: Per altre informazioni su un messaggio, vedere Proprietà messaggio rispetto alla visualizzazione Messaggi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: aae199a21c2806c1472327f620507fac373e09e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120894"
---
# <a name="message-properties-dialog-box"></a>Finestra di dialogo Proprietà messaggio
Usare questa finestra di dialogo per altre informazioni su un messaggio specifico. Per visualizzare questa finestra di dialogo, spostare lo stato attivo su una [finestra Visualizzazione](../debugger/messages-view.md) messaggi. Selezionare un nodo del messaggio nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 La **scheda** Generale è l'unica scheda visualizzata. Sono disponibili le impostazioni seguenti:

 **Handle di finestra** ID univoco di questa finestra. I numeri degli handle di finestra vengono riutilizzati. identificano una finestra solo per la durata di tale finestra. Fare clic su questo valore per visualizzare le proprietà di questa finestra.

 **Livello di annidamento** Profondità di annidamento di questo messaggio, dove 0 non è annidamento.

 **Messaggio** Numero, stato e nome del messaggio di Windows selezionato.

 **lResult** Valore del *parametro lResult,* se presente.

 **wParam** Valore del *parametro wParam,* se presente.

 **lParam** Valore del *parametro lParam,* se presente. Questo valore viene decodificato se è un puntatore a una stringa o a una struttura.

## <a name="related-sections"></a>Sezioni correlate
 [Finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) Consente di selezionare i messaggi elencati nella visualizzazione Messaggi attiva.

 [Finestra di dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md) Usato per trovare il nodo per un messaggio specifico nella visualizzazione Messaggi.

 [Informazioni di riferimento su Spy++](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy++.

 [Apertura della visualizzazione Messaggi dalla finestra Trova](../debugger/how-to-open-messages-view-from-find-window.md) Viene illustrato come aprire la visualizzazione Messaggi dalla finestra di dialogo Trova finestra.

 [Ricerca di un messaggio nella visualizzazione Messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md) Viene illustrato come trovare un messaggio specifico nella visualizzazione Messaggi.

 [Visualizzazione Messaggi](../debugger/messages-view.md) Visualizza il flusso di messaggi associato a una finestra, un processo o un thread.

 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md) Illustra le visualizzazioni albero di Spy++ di finestre, messaggi, processi e thread.

 [Uso di Spy++](../debugger/using-spy-increment.md) Introduce lo strumento Spy++ e spiega come può essere usato.