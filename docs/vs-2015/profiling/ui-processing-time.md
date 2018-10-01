---
title: Periodo di elaborazione dell'interfaccia utente | Microsoft Docs
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
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e35f5f37b0eced2822cb4b019732210bec94495
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531054"
---
# <a name="ui-processing-time"></a>Tempo di elaborazione dell'interfaccia utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [tempo di elaborazione dell'interfaccia utente](https://docs.microsoft.com/visualstudio/profiling/ui-processing-time).  
  
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come Elaborazione interfaccia utente. Ciò implica che un thread stia distribuendo messaggi di Windows o eseguendo altre operazioni dell'interfaccia utente. Durante questo periodo, un thread è stato bloccato in un'API che il visualizzatore di concorrenza conteggia come Elaborazione interfaccia utente. Le interfacce API come `GetMessage()` e `MsgWaitForMultipleObjects()` rientrano in questo gruppo.  
  
 Se non viene identificata alcuna API di blocco predefinita, esaminare gli stack di chiamate e i report di profilatura per determinare la causa del ritardo.  
  
 La categoria Elaborazione interfaccia utente è importante per comprendere la velocità di risposta delle applicazioni GUI ed è pertanto consigliabile nelle applicazioni che dipendono dai tempi di risposta dell'interfaccia utente. Ad esempio, se il thread dell'interfaccia utente in un'applicazione ottiene tempi pari al 100% per Elaborazione interfaccia utente, è probabilmente molto efficiente. Tuttavia, se il thread dell'interfaccia utente impiega molto tempo in altre categorie, cercare le cause principali e prendere in considerazione le opzioni per la riduzione delle categorie non correlate all'interfaccia utente per tale thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)



