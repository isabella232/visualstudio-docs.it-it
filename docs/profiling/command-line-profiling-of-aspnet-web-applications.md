---
title: Profilatura tramite riga di comando di applicazioni Web ASP.NET | Microsoft Docs
description: Informazioni su come usare il Strumenti di profilatura dalla riga di comando per raccogliere dati sulle prestazioni per ASP.NET applicazioni Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 9d551922a3088c7febe07f47d35af04511774a09
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637244"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilatura tramite riga di comando di applicazioni Web ASP.NET
In questa sezione vengono descritte le procedure e le opzioni per la raccolta di dati sulle prestazioni per le applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Strumenti di profilatura dalla riga di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comando.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni Windows 8 e Windows Server 2012 applicazioni](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuto correlato |
| - | - |
| **Raccogliere facilmente dati di profilatura ASP.NET di base:** usare lo strumento **VSPerfASPNETCmd** per raccogliere dati di campionamento, strumentazione, memoria .NET, conflitto o interazione tra livelli senza i requisiti di configurazione e i riavvii di Internet Information Services (IIS) necessari per **VSPerfCmd**. **VSPerfASPNETCmd** non consente di raccogliere dati aggiuntivi o controllare la raccolta dei dati. **Nota:****VSPerfASPNETCmd** è lo strumento preferito per usare il profiler autonomo per profilare ASP.NET siti Web.   | -   [Profilatura rapida di siti Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Raccogliere statistiche delle applicazioni:** usare il metodo di campionamento per raccogliere statistiche delle prestazioni. I dati di campionamento sono utili per analizzare i problemi di utilizzo della CPU e comprendere le caratteristiche generali delle prestazioni delle applicazioni. | -   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Raccogliere dati di intervallo dettagliati:** usare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate. I dati di strumentazione sono utili per analizzare i problemi di I/O e per l'analisi dettagliata degli scenari delle applicazioni. | -   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Raccogliere dati di memoria .NET:** usare il campionamento o la strumentazione per raccogliere dati di allocazione della memoria .NET che illustrano le dimensioni e il numero di oggetti allocati. È anche possibile raccogliere dati sulla durata degli oggetti che mostrano le dimensioni e il numero di oggetti che vengono recuperati a ogni generazione di garbage collection. | -   [Raccogliere dati di memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Raccogliere dati di concorrenza:** usare il metodo di concorrenza per raccogliere i dati relativi ai conflitti di risorse. **Nota:**  La raccolta di dati di visualizzazione e attività dei thread non è supportata per le applicazioni Web. | -   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Aggiungere dati di interazione tra livelli:** È possibile aggiungere dati sulle prestazioni sulle chiamate sincrone [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] effettuate [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dall'applicazione Web a un database [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] Microsoft. | -   [Raccogliere dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Attività correlate

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Profilare applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Sottoporre a profilatura i servizi**|-   [Profilare i servizi](../profiling/command-line-profiling-of-services.md)|
