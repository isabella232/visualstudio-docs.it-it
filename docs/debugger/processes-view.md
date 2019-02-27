---
title: Visualizzazione processi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ba60021410f1965e05f7c5479231013d53cb71
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697624"
---
# <a name="processes-view"></a>Visualizzazione processi
La visualizzazione dei processi viene visualizzato un albero di tutti i processi attivi nel sistema. Vengono visualizzati il nome del modulo e l'ID processo. Se si vuole esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione, usare la visualizzazione dei processi. I processi sono identificati da nomi di modulo o vengono designati come "processi di sistema".

 Microsoft Windows supporta più processi. Ogni processo può avere uno o più thread e ogni thread può avere uno o più associate finestre di primo livello. Ogni finestra di primo livello può disporre di una serie di windows. Un simbolo + indica che un livello è compressa. La visualizzazione compressa è costituito da una riga per ogni processo. Scegliere il simbolo + per espandere il livello.

 Se si vuole esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione, usare la visualizzazione dei processi. I processi sono identificati da nomi di modulo o vengono designati come "processi di sistema". Per trovare un processo, comprimere l'albero e l'elenco di ricerca.

## <a name="procedures"></a>Procedure

#### <a name="to-open-the-processes-view"></a>Per aprire la visualizzazione dei processi

1. Dal **Spy** menu, scegliere **processi**.

   ![Spy&#43; &#43; visualizzazione processi](../debugger/media/spy--_processes.png "Spy + + _Processes") visualizzazione processi di Spy + +

   La figura precedente mostra la visualizzazione dei processi con thread e processi nodi espansi.

### <a name="in-this-section"></a>In questa sezione
 [La ricerca di un processo nella visualizzazione processi](../debugger/how-to-search-for-a-process-in-processes-view.md) viene illustrato come trovare un processo specifico nella visualizzazione processi.

 [Le proprietà del processo visualizzando](../debugger/how-to-display-process-properties.md) viene illustrato come visualizzare altre informazioni su un messaggio.

### <a name="related-sections"></a>Sezioni correlate
 [Visualizzazioni di Spy + +](../debugger/spy-increment-views.md) spiega le visualizzazioni dell'albero Spy + + di windows, i messaggi, processi e thread.

 [Utilizzo di Spy + +](../debugger/using-spy-increment.md) introduce lo strumento Spy + + e spiega come può essere usato.

 [Finestra di dialogo ricerca elabora](../debugger/process-search-dialog-box.md) consente di individuare il nodo per un determinato processo nella visualizzazione processi.

 [Finestra di dialogo Proprietà elabora](../debugger/process-properties-dialog-box.md) vengono visualizzate le proprietà di un processo selezionato nella visualizzazione processi.

 [Riferimenti per Spy + +](../debugger/spy-increment-reference.md) include sezioni che descrivono ogni Spy + + menu e la finestra di dialogo.