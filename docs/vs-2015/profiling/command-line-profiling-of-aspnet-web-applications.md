---
title: Profilatura tramite riga di comando di applicazioni Web ASP.NET | Microsoft Docs
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
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7dd299aac87a03009e39034a3e5282777419506c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541040"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilatura tramite riga di comando di applicazioni Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [della riga di comando di profilatura di applicazioni Web ASP.NET](https://docs.microsoft.com/visualstudio/profiling/command-line-profiling-of-aspnet-web-applications).  
  
Questa sezione descrive le procedure e le opzioni per la raccolta di dati sulle prestazioni per le applicazioni Web di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tramite gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dalla riga di comando.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Raccogliere facilmente dati di profilatura ASP.NET di base:** usare lo strumento **VSPerfASPNETCmd** per raccogliere dati di campionamento, strumentazione, memoria .NET, conflitto o interazione tra livelli senza i requisiti di configurazione e i riavvii di Internet Information Services (IIS) necessari per **VSPerfCmd**. **VSPerfASPNETCmd** non consente di raccogliere dati aggiuntivi o controllare la raccolta dei dati. **Nota:****VSPerfASPNETCmd** è lo strumento preferito da usare se per sottoporre a profilatura siti Web ASP.NET si usa il profiler autonomo.|-   [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Profilatura rapida di un sito Web con VSPerfASPNETCmd)|  
|**Raccogliere statistiche delle applicazioni:** usare il metodo di campionamento per raccogliere statistiche delle prestazioni. I dati di campionamento sono utili per analizzare i problemi di utilizzo della CPU e comprendere le caratteristiche generali delle prestazioni delle applicazioni.|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Raccogliere dati di intervallo dettagliati:** usare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate. I dati di strumentazione sono utili per analizzare i problemi di I/O e per l'analisi dettagliata degli scenari delle applicazioni.|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Raccogliere dati di memoria .NET:** usare il campionamento o la strumentazione per raccogliere dati di allocazione della memoria .NET che illustrano le dimensioni e il numero di oggetti allocati. È anche possibile raccogliere dati sulla durata degli oggetti che mostrano le dimensioni e il numero di oggetti che vengono recuperati a ogni generazione di garbage collection.|-   [Collecting Memory Data](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md) (Raccolta di dati relativi alla memoria)|  
|**Raccogliere dati di concorrenza:** usare il metodo di concorrenza per raccogliere i dati relativi ai conflitti di risorse. **Nota:** la raccolta di dati di attività di thread e di visualizzazione non è supportata per le applicazioni Web.|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati sulle prestazioni relative alle chiamate sincrone [!INCLUDE[vstecado](../includes/vstecado-md.md)] che l'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] esegue nei confronti di un database Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni client autonome**|-   [Profiling Stand-Alone Applications](../profiling/command-line-profiling-of-stand-alone-applications.md) (Profilatura di applicazioni autonome)|  
|**Sottoporre a profilatura i servizi**|-   [Profiling Services](../profiling/command-line-profiling-of-services.md) (Profilatura di servizi)|


