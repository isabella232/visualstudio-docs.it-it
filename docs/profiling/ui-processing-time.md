---
title: Periodo di elaborazione dell'interfaccia utente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad48cd912bfdc117496bc9f876a1a2174e76dc04
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477535"
---
# <a name="ui-processing-time"></a>Periodo di elaborazione dell'interfaccia utente
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come Elaborazione interfaccia utente. Ciò implica che un thread stia distribuendo messaggi di Windows o eseguendo altre operazioni dell'interfaccia utente. Durante questo periodo, un thread è stato bloccato in un'API che il visualizzatore di concorrenza conteggia come Elaborazione interfaccia utente. Le interfacce API come `GetMessage()` e `MsgWaitForMultipleObjects()` rientrano in questo gruppo.  
  
 Se non viene identificata alcuna API di blocco predefinita, esaminare gli stack di chiamate e i report di profilatura per determinare la causa del ritardo.  
  
 La categoria Elaborazione interfaccia utente consente di comprendere la velocità di risposta delle applicazioni GUI ed è pertanto consigliabile nelle applicazioni che dipendono dai tempi di risposta dell'interfaccia utente. Se ad esempio il thread dell'interfaccia utente in un'applicazione ottiene tempi pari al 100% per Elaborazione interfaccia utente, è probabilmente efficiente. Tuttavia, se il thread dell'interfaccia utente impiega molto tempo in altre categorie, cercare le cause principali e prendere in considerazione le opzioni per la riduzione delle categorie non correlate all'interfaccia utente per tale thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)