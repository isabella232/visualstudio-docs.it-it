---
title: 'Riga di comando del profiler: raccogliere le statistiche delle app autonome'
description: Raccogliere statistiche dell'applicazione per le applicazioni autonome usando la riga di comando del profiler in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2dbc5e6dea90f60e5474d27c19a23fc0a10e348ba1ad3529d106555b885c195b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397007"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Raccogliere le statistiche delle applicazioni autonome tramite la riga di comando del profiler
Questa sezione descrive le procedure e le opzioni per la raccolta di statistiche sulle prestazioni per le applicazioni client autonome tramite il metodo di campionamento dalla riga di comando.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni Windows 8 e Windows Server 2012 applicazioni](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuti correlati|
|----------|---------------------|
|**Avviare un'applicazione tramite profilatura**|-   [Procedura: Avviare un'applicazione autonoma e raccogliere statistiche dell'applicazione](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Connettere il profiler a un'applicazione .NET Framework in esecuzione**|-   [Procedura: Connettere il profiler a un'applicazione .NET Framework e raccogliere statistiche dell'applicazione](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Connettere il profiler a un'applicazione C/C++ in esecuzione**|-   [Procedura: Connettere il profiler a un'applicazione nativa e raccogliere statistiche dell'applicazione](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Aggiungere dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-stand-alone-applications"></a>Sottoporre a profilatura applicazioni autonome

|Attività|Contenuti correlati|
|----------|---------------------|
|**Instrumentare un'applicazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Raccolta di dati di allocazione di memoria .NET e garbage collection**|-   [Raccogliere dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Raccogliere dati sui conflitti di risorse e sull'esecuzione di thread**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Eseguire la profilatura tramite il metodo di campionamento

|Attività|Contenuti correlati|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni Web ASP.NET**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Sottoporre a profilatura i servizi**|-   [Raccogliere statistiche dell'applicazione usando il campionamento.](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) Descrive come raccogliere statistiche sulle prestazioni da servizi Windows tramite il metodo di campionamento.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di campionamento
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
