---
title: Raccolta di dati di intervallo dettagliati per un'applicazione Web ASP.NET usando il metodo di strumentazione del profiler tramite la riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eabd6d66079fc003bb87e867c0b5bb572c3bddc1
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590490"
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Raccolta di dati di intervallo dettagliati per un'applicazione Web ASP.NET utilizzando il metodo di strumentazione del profiler tramite la riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Collecting intervallo dati dettagliati per un'applicazione Web ASP.NET usando il metodo di strumentazione del Profiler da riga di comando](https://docs.microsoft.com/visualstudio/profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line).  
  
Questa sezione descrive le procedure e le opzioni per la raccolta di dati dettagliati sulle prestazioni per un'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] usando lo strumento della riga di comando **VSPerfCmd** e il metodo di strumentazione.  
  
> [!NOTE]
>  Lo strumento **VSPerfCmd** consente l'accesso completo alle funzionalità degli strumenti di profilatura, tra cui la sospensione e la ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e dai contatori delle prestazioni di Windows. Quando queste funzionalità non sono necessarie è anche possibile usare lo strumento da riga di comando **VSPerfASPNETCmd**. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente e non è richiesto il riavvio del computer. Per altre informazioni, vedere [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Profilatura rapida di un sito Web con VSPerfASPNETCmd).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Profilare file binari compilati in modo statico**|-   [Procedura: instrumentare un'applicazione ASP.NET compilata in modo statico e raccogliere dati di intervallo dettagliati](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Profilare file binari compilati in modo dinamico**|-   [Procedura: Instrumentare un'applicazione ASP.NET compilata in modo dinamico e raccogliere dati di intervallo dettagliati](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
### <a name="profiling-aspnet-web-applications"></a>Profilatura di applicazioni Web ASP.NET  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profilatura dell'allocazione di memoria e garbage collection**|-   [Collecting Memory Data](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md) (Raccolta di dati relativi alla memoria)|  
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>Profilatura tramite il metodo di strumentazione  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Sottoporre a profilatura i servizi**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>Analisi di visualizzazioni dati e di report di strumentazione  
 [Instrumentation Method Data Views](../profiling/instrumentation-method-data-views.md) (Visualizzazioni dei dati del metodo di strumentazione)



