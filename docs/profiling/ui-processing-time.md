---
title: Periodo di elaborazione dell'interfaccia utente | Microsoft Docs
description: Informazioni sul fatto che i segmenti nella sequenza temporale sono associati a tempi di blocco classificati come elaborazione dell'interfaccia utente.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 160200ebb40f99ce2f22086d5904995cc54e9a80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141051"
---
# <a name="ui-processing-time"></a>Periodo di elaborazione dell'interfaccia utente
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come Elaborazione interfaccia utente. Ciò implica che un thread stia distribuendo messaggi di Windows o eseguendo altre operazioni dell'interfaccia utente. Durante questo periodo, un thread è stato bloccato in un'API che il visualizzatore di concorrenza conteggia come Elaborazione interfaccia utente. Le interfacce API come `GetMessage()` e `MsgWaitForMultipleObjects()` rientrano in questo gruppo.

 Se non viene identificata alcuna API di blocco predefinita, esaminare gli stack di chiamate e i report di profilatura per determinare la causa del ritardo.

 La categoria Elaborazione interfaccia utente consente di comprendere la velocità di risposta delle applicazioni GUI ed è pertanto consigliabile nelle applicazioni che dipendono dai tempi di risposta dell'interfaccia utente. Se ad esempio il thread dell'interfaccia utente in un'applicazione ottiene tempi pari al 100% per Elaborazione interfaccia utente, è probabilmente efficiente. Tuttavia, se il thread dell'interfaccia utente impiega molto tempo in altre categorie, cercare le cause principali e prendere in considerazione le opzioni per la riduzione delle categorie non correlate all'interfaccia utente per tale thread.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)