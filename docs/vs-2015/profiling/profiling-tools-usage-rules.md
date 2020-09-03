---
title: Regole di utilizzo degli strumenti di profilatura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4158a6a393ed6e64dedddfca10c1ae04a95e3d3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535551"
---
# <a name="profiling-tools-usage-rules"></a>Regole di utilizzo degli strumenti di profilatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le regole delle prestazioni nella categoria di utilizzo degli strumenti di profilatura forniscono indicazioni per l'uso del profiler per una raccolta più efficiente dei dati.  
  
|Regola|Descrizione|  
|-|-|  
|[DA0002: VSPerfCorProf.dll mancante](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|La profilatura dalla riga di comando potrebbe contenere dati incompleti per i file binari di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Il problema può essere causato dalla mancata impostazione delle variabili di ambiente corrette.|  
|[DA0003: Numero elevato di campioni del kernel](../profiling/da0003-many-kernel-samples.md)|Sono stati registrati molti campioni di profilatura che si sono verificati all'esterno dell'esecuzione del file binario di destinazione. Per raccogliere dati più accurati, è consigliabile ricorrere al metodo di strumentazione.|  
|[DA0004: Utilizzo elevato del processore](../profiling/da0004-high-processor-usage.md)|I dati di profilatura indicano che i processori sono stati occupati in modo costante durante l'esecuzione della profilatura. Per raccogliere dati più accurati, è consigliabile ricorrere al metodo di campionamento.|  
|[DA0008: Numero ridotto di campioni raccolti](../profiling/da0008-few-samples-collected.md)|Il numero di campioni raccolti nell'esecuzione della profilatura non è sufficiente per essere statisticamente significativo. È consigliabile rieseguire la profilatura mantenendo l'applicazione in esecuzione per un periodo di tempo più lungo. È anche possibile considerare l'uso del metodo di strumentazione per la raccolta dei dati.|  
|[DA0026: Tempo di elaborazione CPU kernel eccessivo](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|L'esecuzione della profilatura in modalità kernel del processore ha richiesto un periodo di tempo notevole. Considerare l'uso del metodo di campionamento usando come metrica le chiamate di sistema anziché il tempo.|  
|[DA0029: Versione CLR non supportata](../profiling/da0029-unsupported-clr-version.md)|Il file binario profilato usa una versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] non supportata dal profiler. I rapporti del profiler indicano che non è possibile risolvere i nomi dei simboli.|  
|[DA0030: Raccogliere misurazioni di interazione tra livelli per i progetti di database](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|È stato raccolto un numero significativo di chiamate ai metodi nello spazio dei nomi <xref:System.Data?displayProperty=fullName>. Per includere i dati sulle chiamate di database, prendere in considerazione la raccolta dei dati sull'interazione tra livelli nelle esecuzioni di profilatura.|
