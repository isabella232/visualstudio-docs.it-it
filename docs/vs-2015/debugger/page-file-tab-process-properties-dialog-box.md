---
title: Scheda File di paging, finestra di dialogo Proprietà processo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3394d2b71fad7b9d611bc4392f55d4518766665
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209339"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Scheda File di paging, finestra di dialogo Proprietà processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usare la **File di paging** pressione di tab per esaminare il file di paging di un processo. Per visualizzare il [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su un [visualizzazione processi](../debugger/processes-view.md) finestra. Selezionare qualsiasi nodo del processo nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.  
  
 Le impostazioni seguenti sono disponibili sul **File di paging** scheda:  
  
|Voce|Descrizione|  
|-----------|-----------------|  
|**Byte File di paging**|Il numero corrente di pagine che usa questo processo nel file di paging. Il file di paging vengono archiviate le pagine di dati usata dal processo ma non contenute in altri file. Il file di paging viene usato da tutti i processi e la mancanza di spazio nel file di paging può provocare errori mentre sono in esecuzione altri processi.|  
|**Numero massimo byte di File di paging**|Il numero massimo di pagine in cui il processo ha usato nel file di paging.|  
|**Errori di pagina**|Il numero di errori di pagina nei thread in esecuzione in questo processo. Un errore di pagina si verifica quando un thread fa riferimento a una pagina di memoria virtuale che non è presente nel proprio working set della memoria principale. Di conseguenza, la pagina non essere richiamata dal disco se presente nell'elenco di standby e quindi già nella memoria principale o se è in uso da un altro processo con cui pagina è condivisa.|



