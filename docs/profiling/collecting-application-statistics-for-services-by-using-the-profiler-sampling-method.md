---
title: Raccogliere statistiche per i servizi Windows - metodo di campionamento del profiler
description: Esaminare le procedure e le opzioni per raccogliere statistiche sulle prestazioni per Windows usando il metodo di campionamento di profilatura dalla riga di comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bbb825bc851238ce2b0be98cc30921ca4a389bfe17d42e090566e8bd4997ddbf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333756"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Raccogliere le statistiche dell'applicazione per i servizi tramite il metodo di campionamento del profiler
Questa sezione descrive le procedure e le opzioni per la raccolta di statistiche sulle prestazioni per i servizi Windows tramite il metodo di campionamento dalla riga di comando.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Connettere il profiler a un servizio .NET**|-   [Procedura: Connettere il profiler a un servizio .NET per raccogliere statistiche dell'applicazione](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Aggiungere dati di interazione tra livelli**|-   [Raccogliere i dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Connettere il profiler a un servizio C/C++**|-   [Procedura: Connettere il profiler a un servizio nativo per raccogliere statistiche dell'applicazione](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-windows-services"></a>Profilare servizi Windows

|Attività|Contenuto correlato|
|----------|---------------------|
|**Profilare usando il metodo di strumentazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Raccogliere dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Eseguire la profilatura tramite il metodo di campionamento

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilare ASP.NET applicazioni Web**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di campionamento
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
