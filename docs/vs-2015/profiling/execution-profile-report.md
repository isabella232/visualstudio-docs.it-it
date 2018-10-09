---
title: Rapporto profilo di esecuzione| Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6e13e18857ce67bc5d333fb2d91b2df97fdc08d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528126"
---
# <a name="execution-profile-report"></a>Report del profilo di esecuzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [rapporto profilo di esecuzione](https://docs.microsoft.com/visualstudio/profiling/execution-profile-report).  
  
Il rapporto del profilo di esecuzione è un profilo di campionamento tradizionale. I campioni vengono presi ogni millisecondo circa durante i periodi in cui un thread è in esecuzione su un core logico e il visualizzatore di concorrenza compila un albero delle chiamate tipico collazionando il set di stack di campioni accumulato. I dati della tabella possono essere influenzati dall'intervallo di tempo corrente e dai thread nascosti e dai filtri seguenti che possono essere applicati:  
  
-   Se l'opzione Just My Code è selezionata, vengono visualizzati solo gli stack frame con codice utente, più un livello sotto il codice utente.  
  
-   Se è impostato il valore di Riduzione rumore, gli stack collazionati con una frequenza minore di quella specificata vengono esclusi dal filtro.  
  
 Nella tabella seguente vengono illustrate le colonne del rapporto.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|nome|Nome della funzione per ogni livello dello stack di chiamate.|  
|Campioni inclusivi|Numero totale di campioni raccolti per tutti gli stack accumulati nel livello dell'albero dello stack di chiamate. Il numero inclusivo è la somma dei campioni esclusivi per questa funzione e dei contatori inclusivi per tutti i nodi figlio.|  
|Campioni esclusivi|Numero totale di campioni raccolti per cui questa funzione è il livello più basso dello stack di chiamate.|  
|% inclusivi|La percentuale di campioni totali visualizzata nella colonna dei campioni inclusivi. Le percentuali vengono arrotondate a due cifre decimali.|  
|% esclusivi|La percentuale di campioni totali visualizzata nella colonna dei campioni esclusivi. Le percentuali vengono arrotondate a due cifre decimali.|  
|Dettagli|Nome completo della funzione. Include il conteggio delle righe, se disponibile.|  
  
 Questa tabella di rapporto viene illustrata in [Tempo di esecuzione (Visualizzazione thread)](../profiling/execution-time-threads-view.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)


