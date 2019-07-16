---
title: Raccolta di dati di concorrenza per applicazioni autonome tramite la riga di comando del profiler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fac1c840d93c03b659e7934a82eb53895b60ede
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68141946"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Raccolta di dati di concorrenza per applicazioni autonome tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il metodo di concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema.  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Avviare un'applicazione .NET Framework e sottoporre a profilatura dati di concorrenza**|-   [Procedura: Avviare un'applicazione .NET Framework per raccogliere dati di concorrenza](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Avviare un'applicazione C/C++ e sottoporre a profilatura dati di concorrenza**|-   [Procedura: Avviare un'applicazione nativa per raccogliere dati di concorrenza](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Connettere il profiler a un'applicazione .NET Framework in esecuzione**|-   [Procedura: Connettere il profiler a un'applicazione .NET Framework per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Connettere il profiler a un'applicazione C/C++ in esecuzione**|-   [Procedura: Connettere il profiler a un'applicazione nativa e raccogliere dati di concorrenza](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-stand-alone-applications"></a>Profilatura di applicazioni autonome  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Raccolta di dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Aggiunta di dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Profilatura di problemi di concorrenza  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni ASP.NET**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura i servizi**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di concorrenza  
 [Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)  
  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Riferimenti  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)
