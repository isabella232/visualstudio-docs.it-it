---
title: Raccolta di dati di concorrenza per un servizio tramite la riga di comando del profiler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2764116c6e502af76b9577cf4752a6d3b19f0986
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760112"
---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Raccolta di dati di concorrenza per un servizio tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il metodo di concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Connettersi a un servizio .NET in esecuzione**|-   [Procedura: Connettere il profiler a un servizio .NET per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Aggiungere dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Connettersi a un servizio C/C++ in esecuzione**|-   [Procedura: Connettere il profiler a un servizio natvo per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-windows-services"></a>Profilatura di servizi Windows  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Sottoporre a profilatura tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Collecting .NET Memory Data](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) (Raccolta di dati di memoria .NET)|  
  
### <a name="profiling-concurrency-data"></a>Profilatura di dati di concorrenza  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni autonome**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura applicazioni Web ASP.NET**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di concorrenza  
 [Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)  
  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Riferimenti  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)
