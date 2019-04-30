---
title: Profilatura tramite riga di comando di applicazioni Web ASP.NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c93cb4774953f1425ff0330d7f588cbbf0f0b823
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439014"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilatura tramite riga di comando di applicazioni Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa sezione descrive le procedure e le opzioni per la raccolta di dati sulle prestazioni per le applicazioni Web di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tramite gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dalla riga di comando.  
  
> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Raccogliere facilmente dati di profilatura ASP.NET di base:** usare lo strumento **VSPerfASPNETCmd** per raccogliere dati di campionamento, strumentazione, memoria .NET, contesa o interazione tra livelli senza i requisiti di configurazione e i riavvii di Internet Information Services (IIS) necessari per **VSPerfCmd**. **VSPerfASPNETCmd** non consente di raccogliere dati aggiuntivi o controllare la raccolta dei dati. **Nota:**  **VSPerfASPNETCmd** è lo strumento preferito da usare se per sottoporre a profilatura siti Web ASP.NET si usa il profiler autonomo.|-   [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Profilatura rapida di un sito Web con VSPerfASPNETCmd)|  
|**Raccogliere statistiche dell'applicazione:** usare il metodo di campionamento per raccogliere statistiche sulle prestazioni. I dati di campionamento sono utili per analizzare i problemi di utilizzo della CPU e comprendere le caratteristiche generali delle prestazioni delle applicazioni.|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Raccogliere dati di intervallo dettagliati:** usare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate. I dati di strumentazione sono utili per analizzare i problemi di I/O e per l'analisi dettagliata degli scenari delle applicazioni.|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Raccogliere dati di memoria .NET:** usare il campionamento o la strumentazione per raccogliere dati di allocazione della memoria .NET che indicano le dimensioni e il numero di oggetti allocati. È anche possibile raccogliere dati sulla durata degli oggetti che mostrano le dimensioni e il numero di oggetti che vengono recuperati a ogni generazione di garbage collection.|-   [Collecting Memory Data](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md) (Raccolta di dati relativi alla memoria)|  
|**Raccogliere dati di concorrenza:** usare il metodo di concorrenza per raccogliere i dati relativi alle contese di risorse. **Nota:**  la raccolta di dati di attività di thread e di visualizzazione non è supportata per le applicazioni Web.|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati sulle prestazioni relative alle chiamate sincrone [!INCLUDE[vstecado](../includes/vstecado-md.md)] che l'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] esegue nei confronti di un database Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Contenuto correlato|  
|----------|---------------------|  
|**Sottoporre a profilatura applicazioni client autonome**|-   [Profiling Stand-Alone Applications](../profiling/command-line-profiling-of-stand-alone-applications.md) (Profilatura di applicazioni autonome)|  
|**Sottoporre a profilatura i servizi**|-   [Profiling Services](../profiling/command-line-profiling-of-services.md) (Profilatura di servizi)|
