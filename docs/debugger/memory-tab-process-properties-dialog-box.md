---
title: Scheda Memoria, finestra di dialogo Proprietà processo | Microsoft Docs
description: Usare la scheda Memoria di Proprietà processo per visualizzare il modo in cui un processo usa la memoria. Sono disponibili informazioni sullo spazio usato, lo spazio condiviso e lo spazio virtuale usato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 65171b796f440bc612bb7e0802bacd2373b23eb6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709904"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Scheda Memoria, finestra di dialogo Proprietà processo
Usare la **scheda Memoria** per mostrare come un processo usa la memoria. Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione](../debugger/processes-view.md) processi. Selezionare un nodo di processo nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 Nella scheda Memoria sono disponibili **le impostazioni** seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Virtual Bytes**|Dimensione corrente (in byte) dello spazio degli indirizzi virtuali utilizzato dal processo. L'uso dello spazio indirizzi virtuali non implica necessariamente l'uso corrispondente delle pagine di memoria principale o del disco. Tuttavia, lo spazio virtuale è finito e l'uso di troppo può limitare la capacità del processo di caricare le librerie.|
|**N. massimo byte virtuali**|Numero massimo di byte di spazio degli indirizzi virtuali usato dal processo in qualsiasi momento.|
|**Working Set**|Set di pagine di memoria toccate di recente dai thread nel processo. Se la memoria disponibile nel computer supera la soglia specificata, le pagine verranno lasciate nel working set di un processo anche se non sono utilizzate. Quando la memoria disponibile scende sotto una soglia, le pagine vengono tagliate dal working set. Se necessario, gli errori verranno nuovamente visualizzati nel working set prima di lasciare la memoria principale.|
|**Working Set massimo**|Numero massimo di pagine nel working set di questo processo in qualsiasi momento.|
|**Byte riserva di paging**|Quantità corrente di pool di paging allocata dal processo. Il pool di paging è un'area di memoria di sistema in cui i componenti del sistema operativo acquisiscono spazio durante l'esecuzione delle attività di controllo. È possibile eseguire il paging delle pagine del pool di paging nel file di paging quando il sistema non accede per periodi di tempo prolungati.|
|**Byte riserva non di paging**|Numero corrente di byte nel pool non di paging allocato dal processo. Il pool non di paging è un'area di memoria di sistema in cui lo spazio viene acquisito dai componenti del sistema operativo durante l'esecuzione delle attività necessarie. Non è possibile eseguire il paging delle pagine del pool non di paging nel file di paging. rimangono nella memoria principale finché vengono allocate.|
|**Private Bytes**|Numero corrente di byte allocati da questo processo che non possono essere condivisi con altri processi.|
|**Byte liberi**|Spazio totale degli indirizzi virtuali inutilizzati di questo processo.|
|**Byte riservati**|Quantità totale di memoria virtuale riservata per l'uso futuro da parte di questo processo.|
|**Byte immagine liberi**|Quantità di spazio degli indirizzi virtuali non in uso o riservato dalle immagini all'interno di questo processo.|
|**Byte immagine riservati**|Somma di tutta la memoria virtuale riservata dalle immagini eseguite all'interno di questo processo.|