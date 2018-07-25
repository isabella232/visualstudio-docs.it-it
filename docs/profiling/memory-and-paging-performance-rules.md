---
title: Regole di prestazioni relative a memoria e paging | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec1acb6763d408f9f13ec3044e2cd8137d34e634
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237653"
---
# <a name="memory-and-paging-performance-rules"></a>Regole di prestazioni relative a memoria e paging
Le regole di prestazioni nelle categoria memoria e paging identificano l'attività di paging in un'esecuzione di profilatura che può influire sulla velocità di risposta e le prestazioni dell'applicazione.  
  
|||  
|-|-|  
|[DA0014: Frequenze molto elevate di paging di memoria attiva su disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Durante l'esecuzione della profilatura è stata rilevata una frequenza estremamente elevata di paging di memoria attiva da e verso il disco. In genere, le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione. Provare a eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria. Questa regola viene attivata quando la quantità di attività di paging supera la soglia superiore della regola D0017.|  
|[DA0017: Frequenze elevate di paging di memoria attiva su disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Durante l'esecuzione della profilatura è stata rilevata una frequenza relativamente elevata di paging di memoria attiva da e verso il disco. In genere, le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione. Provare a eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria.|