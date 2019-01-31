---
title: Scheda memoria, finestra di dialogo Proprietà processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccafbcf829b78fa4e1c12b3a46c46dfa59e3e863
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996402"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Scheda Memoria, finestra di dialogo Proprietà processo
Usare la **memoria** scheda per visualizzare l'utilizzo della memoria da parte di un processo. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **memoria** scheda:  
  
|Voce|Description|  
|-----------|-----------------|  
|**Byte virtuali**|Le dimensioni correnti (in byte) di spazio degli indirizzi virtuali usata dal processo. L'utilizzo di spazio degli indirizzi virtuali non implica necessariamente un uso corrispondente di pagine su disco o memoria principale. Tuttavia, lo spazio virtuale è finito e usando troppa può limitare la capacità del processo per caricare le librerie.|  
|**N. massimo byte virtuali**|Il numero massimo di byte di spazio degli indirizzi virtuali del processo è utilizzato in qualsiasi momento.|  
|**Working Set**|Il set di pagine in memoria utilizzate di recente dai thread del processo. Se la memoria disponibile è superiore alla soglia specificata, le pagine verranno lasciate nel Working Set di un processo anche se non sono in uso. Quando la memoria disponibile scende sotto una soglia, le pagine verranno rimosse dal Working Set. Se sono necessarie, saranno richiamate nuovamente nel Working Set prima di lasciare la memoria principale.|  
|**Working Set massimo**|Il numero massimo di pagine nel working set del processo in qualsiasi punto nel tempo.|  
|**Byte riserva di paging**|La quantità corrente di pool di paging allocata dal processo. Pool di paging è un'area di memoria di sistema in cui i componenti del sistema operativo acquisiscono spazio come il completamento delle attività assegnate. Le pagine del pool di paging possono essere trasferite nel file di paging quando non si accede dal sistema per periodi prolungati di tempo.|  
|**Byte riserva non di paging**|Numero corrente di byte in pool non di paging allocata dal processo. Il pool non di paging è un'area di memoria di sistema in cui lo spazio viene acquisito da componenti del sistema operativo come il completamento delle attività assegnate. Le pagine del pool non di paging non possono essere trasferite nel file di paging; rimangono nella memoria principale fino a quando vengono allocate.|  
|**Byte privati**|Il numero corrente di byte, allocata a questo processo che non può essere condivisi con altri processi.|  
|**Byte liberi**|Lo spazio indirizzi virtuali inutilizzati totale di questo processo.|  
|**Byte riservati**|La quantità totale di memoria virtuale riservata per utilizzi futuri da questo processo.|  
|**Byte immagine liberi**|La quantità di spazio degli indirizzi virtuali che non sia in uso o riservato per le immagini all'interno di questo processo.|  
|**Byte immagine riservati**|La somma della memoria virtuale riservata per le immagini eseguito all'interno di questo processo.|