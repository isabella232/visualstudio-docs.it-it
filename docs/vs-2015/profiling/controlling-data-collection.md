---
title: Controllo della raccolta di dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e34c4db965cacefabe752774e393a4339042040e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182715"
---
# <a name="controlling-data-collection"></a>Controllo della raccolta di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consentono di controllare quando i dati di profilatura vengono raccolti durante una sessione prestazioni e di specificare le funzioni che vengono profilate. In questa sezione viene descritto come avviare e arrestare la raccolta dei dati dalle finestre **Esplora prestazioni** e **Controllo raccolta dati** e come limitare gli oggetti per i quali vengono raccolti i dati di profilatura.  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Avviare e interrompere la profilatura:** è possibile avviare la profilatura di un'applicazione all'avvio dell'applicazione, oppure collegare il profiler a un processo già in esecuzione. Quando l'applicazione di destinazione è in esecuzione, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura chiudere l'applicazione di destinazione o disconnettere il profiler da un processo in esecuzione.|-   [Procedura: iniziare e terminare la raccolta dei dati sulle prestazioni](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Procedura: connettere e disconnettere gli strumenti per le prestazioni ai processi in esecuzione](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Procedura: sospendere e riprendere la raccolta dei dati sulle prestazioni](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Configurare la profilatura della strumentazione per limitare i dati raccolti:** è possibile usare la configurazione della sessione prestazioni per limitare i dati raccolti durante le esecuzioni della profilatura che usano il metodo di strumentazione. È possibile includere o escludere specifici file con estensione dll, spazi dei nomi, classi e funzioni. È anche possibile escludere le funzioni che non soddisfano una soglia di dimensioni specificata.|-   [Procedura: limitare la strumentazione a specifiche dll](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Procedura: limitare la strumentazione a funzioni specifiche](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Procedura: escludere o includere funzioni brevi dalla strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esplora prestazioni](../profiling/performance-explorer.md)
