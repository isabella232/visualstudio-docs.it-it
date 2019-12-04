---
title: Usare la riga di comando del profiler per ottenere dati sulla concorrenza per il servizio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b7b60ad871f40e06e2a8fbf6782773ce6596f31
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779675"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Raccogliere dati di concorrenza per un servizio tramite la riga di comando del profiler
Il metodo di concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Connettersi a un servizio .NET in esecuzione**|-   [Procedura: Connettere il profiler a un servizio .NET per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Aggiungere dati di interazione tra livelli**|-   [Raccogliere dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Connettersi a un servizio C/C++ in esecuzione**|-   [Procedura: Connettere il profiler a un servizio nativo per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-windows-services"></a>Profilare servizi Windows

|Attività|Contenuto correlato|
|----------|---------------------|
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Sottoporre a profilatura tramite il metodo di strumentazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Raccogliere dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Sottoporre a profilatura dati di concorrenza

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni autonome**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Sottoporre a profilatura applicazioni Web ASP.NET**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di concorrenza
- [Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)

- [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Reference
- [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)
