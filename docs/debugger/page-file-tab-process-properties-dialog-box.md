---
title: Scheda File di paging, finestra di dialogo Proprietà processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d45fa813a7bb75ea0cdd11a412ae35e5444883dc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924963"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Scheda File di paging, finestra di dialogo Proprietà processo
Usare la **File di paging** pressione di tab per esaminare il file di paging di un processo. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **File di paging** scheda:  
  
|Voce|Description|  
|-----------|-----------------|  
|**Byte file di paging**|Il numero corrente di pagine che usa questo processo nel file di paging. Il file di paging vengono archiviate le pagine di dati usata dal processo ma non contenute in altri file. Il file di paging viene usato da tutti i processi e la mancanza di spazio nel file di paging può provocare errori mentre sono in esecuzione altri processi.|  
|**N. max byte file di paging**|Il numero massimo di pagine in cui il processo ha usato nel file di paging.|  
|**Errori di pagina**|Il numero di errori di pagina nei thread in esecuzione in questo processo. Un errore di pagina si verifica quando un thread fa riferimento a una pagina di memoria virtuale che non è presente nel proprio working set della memoria principale. Di conseguenza, la pagina non essere richiamata dal disco se presente nell'elenco di standby e quindi già nella memoria principale o se è in uso da un altro processo con cui pagina è condivisa.|