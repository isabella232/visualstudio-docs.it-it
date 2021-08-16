---
title: Regole di prestazioni relative a memoria e paging | Microsoft Docs
description: Informazioni su come le regole delle prestazioni nella categoria memoria e paging identificano l'attività di paging in un'esecuzione della profilatura che può influire sulle prestazioni e sulla velocità di risposta dell'applicazione.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 71697bcfd375217ca54be591ec18b334369853b0e1a71bccb5aa2bdb27a41058
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410463"
---
# <a name="memory-and-paging-performance-rules"></a>Regole di prestazioni relative a memoria e paging
Le regole di prestazioni nelle categoria memoria e paging identificano l'attività di paging in un'esecuzione di profilatura che può influire sulla velocità di risposta e le prestazioni dell'applicazione.

|Regola|Descrizione|
|-|-|
|[DA0014: Frequenze molto elevate di paging di memoria attiva su disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Durante l'esecuzione della profilatura è stata rilevata una frequenza estremamente elevata di paging di memoria attiva da e verso il disco. In genere, le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione. Provare a eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria. Questa regola viene attivata quando la quantità di attività di paging supera la soglia superiore della regola D0017.|
|[DA0017: Frequenze elevate di paging di memoria attiva su disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Durante l'esecuzione della profilatura è stata rilevata una frequenza relativamente elevata di paging di memoria attiva da e verso il disco. In genere, le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione. Provare a eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria.|
