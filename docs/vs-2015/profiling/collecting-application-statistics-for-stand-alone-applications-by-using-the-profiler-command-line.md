---
title: Raccolta delle statistiche delle applicazioni autonome tramite la riga di comando del profiler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03e27d021b8b3c5ec29a8646a1bbe7bc6ebdecc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839936"
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Raccolta delle statistiche delle applicazioni autonome tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione descrive le procedure e le opzioni per la raccolta di statistiche sulle prestazioni per le applicazioni client autonome tramite il metodo di campionamento dalla riga di comando.  
  
> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Avviare un'applicazione tramite profilatura**|-   [How to: Launch a Stand-Alone Application and Collect Application Statistics](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md) (Procedura: Avviare un'applicazione autonoma e raccogliere statistiche dell'applicazione)|  
|**Connettere il profiler a un'applicazione .NET Framework in esecuzione**|-   [How to: Attach the Profiler to a .NET Framework Application and Collect Application Statistics](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md) (Procedura: Connettere il profiler a un'applicazione .NET Framework e raccogliere statistiche dell'applicazione)|  
|**Connettere il profiler a un'applicazione C/C++ in esecuzione**|-   [How to: Attach the Profiler to a Native Application and Collect Application Statistics](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md) (Procedura: connettere il profiler a un'applicazione nativa e raccogliere statistiche dell'applicazione)|  
|**Aggiungere dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-stand-alone-applications"></a>Profilatura di applicazioni autonome  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Instrumentare un'applicazione**|-   [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Raccolta di dati di allocazione di memoria .NET e garbage collection**|-   [Raccolta di dati di memoria .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Raccogliere dati sui conflitti di risorse e sull'esecuzione di thread**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilatura tramite il metodo di campionamento  
  
|Attività|Contenuti correlati|  
|----------|---------------------|  
|**Profilare applicazioni Web ASP.NET**|-   [Raccolta delle statistiche dell'applicazione tramite campionamento](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
|**Sottoporre a profilatura i servizi**|-   [Raccolta delle statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Descrive come raccogliere statistiche sulle prestazioni da servizi Windows tramite il metodo di campionamento.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di campionamento  
 [Visualizzazioni dei dati dei metodi di campionamento](../profiling/profiler-sampling-method-data-views.md)
