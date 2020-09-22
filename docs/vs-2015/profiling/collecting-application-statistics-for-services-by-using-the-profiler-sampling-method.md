---
title: Raccolta delle statistiche dell'applicazione per i servizi tramite il metodo di campionamento del profiler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f556a039ab131a563a90010112009b39f4c981
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839427"
---
# <a name="collecting-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Raccolta delle statistiche dell'applicazione per i servizi tramite il metodo di campionamento del profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione descrive le procedure e le opzioni per la raccolta di statistiche sulle prestazioni per i servizi Windows tramite il metodo di campionamento dalla riga di comando.  
  
> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Connettere il profiler a un servizio .NET**|-   [How to: Attach the Profiler to a .NET Service to Collect Application Statistics](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md) (Procedura: Connettere il profiler a un servizio .NET per raccogliere statistiche dell'applicazione)|  
|**Aggiungere dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Connettere il profiler a un servizio C/C++**|-   [How to: Attach the Profiler to a Native Service to Collect Application Statistics](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md) (Procedura: Connettere il profiler a un servizio nativo per raccogliere statistiche dell'applicazione)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-windows-services"></a>Profilatura di servizi Windows  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Profilare usando il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Raccolta di dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilatura tramite il metodo di campionamento  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccolta delle statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profilare applicazioni Web ASP.NET**|-   [Raccolta delle statistiche dell'applicazione tramite campionamento](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di campionamento  
 [Visualizzazioni dei dati dei metodi di campionamento](../profiling/profiler-sampling-method-data-views.md)
