---
title: Visualizzazione processi | Microsoft Docs
description: La visualizzazione Processi visualizza un albero di tutti i processi attivi nel sistema. Informazioni sul contenuto e sugli usi e collegamenti ad altre informazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b7030c8bc6f8df01579640f02fc22dce07f46d5f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090538"
---
# <a name="processes-view"></a>Visualizzazione processi
Nella visualizzazione Processi viene visualizzato un albero di tutti i processi attivi nel sistema. Vengono visualizzati l'ID del processo e il nome del modulo. Usare la visualizzazione Processi se si vuole esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione. I processi sono identificati dai nomi dei moduli o sono designati come "processi di sistema".

 Microsoft Windows supporta più processi. Ogni processo può avere uno o più thread e ogni thread può avere una o più finestre di primo livello associate. Ogni finestra di primo livello può essere proprietaria di una serie di finestre. Un simbolo + indica che un livello è compresso. La visualizzazione compressa è costituita da una riga per processo. Fare clic sul simbolo + per espandere il livello.

 Usare la visualizzazione Processi se si vuole esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione. I processi sono identificati dai nomi dei moduli o sono designati come "processi di sistema". Per trovare un processo, comprimere l'albero ed eseguire ricerche nell'elenco.

## <a name="procedures"></a>Procedure

#### <a name="to-open-the-processes-view"></a>Per aprire la visualizzazione Processi

1. Scegliere Processi dal menu **Spy.**

   ![Visualizzazione processi&#43;&#43; Spy](../debugger/media/spy--_processes.png "Spy++_Processes") Visualizzazione processi di Spy++

   La figura precedente mostra la visualizzazione Processi con i nodi di processo e thread espansi.

### <a name="in-this-section"></a>Contenuto della sezione
 [Ricerca di un processo nella visualizzazione Processi](../debugger/how-to-search-for-a-process-in-processes-view.md) Viene illustrato come trovare un processo specifico nella visualizzazione Processi.

 [Visualizzazione delle proprietà del processo](../debugger/how-to-display-process-properties.md) Viene illustrato come visualizzare altre informazioni su un messaggio.

### <a name="related-sections"></a>Sezioni correlate
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md) Illustra le visualizzazioni albero di Spy++ di finestre, messaggi, processi e thread.

 [Uso di Spy++](../debugger/using-spy-increment.md) Introduce lo strumento Spy++ e spiega come può essere usato.

 [Finestra di dialogo Elabora ricerca](../debugger/process-search-dialog-box.md) Usato per trovare il nodo per un processo specifico nella visualizzazione Processi.

 [Finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md) Visualizza le proprietà di un processo selezionato nella visualizzazione Processi.

 [Informazioni di riferimento su Spy++](../debugger/spy-increment-reference.md) Include sezioni che descrivono ogni menu e finestra di dialogo di Spy++.