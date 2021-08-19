---
title: Riga di comando del profiler - Ottenere i dati di concorrenza delle app autonome
description: Raccogliere dati di concorrenza per le applicazioni autonome usando la riga di comando del profiler in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d5b02fb61082f1bea1936e4590c8fd7f478ea60
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093346"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Raccogliere dati di concorrenza per applicazioni autonome tramite la riga di comando del profiler
Il metodo di concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema.

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuti correlati|
|----------|---------------------|
|**Avviare un'applicazione .NET Framework e sottoporre a profilatura dati di concorrenza**|-   [Procedura: Avviare un'.NET Framework per raccogliere dati di concorrenza](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Avviare un'applicazione C/C++ e sottoporre a profilatura dati di concorrenza**|-   [Procedura: Avviare un'applicazione nativa per raccogliere dati di concorrenza](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Connettere il profiler a un'applicazione .NET Framework in esecuzione**|-   [Procedura: Connettere il profiler a un'.NET Framework per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Connettere il profiler a un'applicazione C/C++ in esecuzione**|-   [Procedura: Connettere il profiler a un'applicazione nativa e raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-stand-alone-applications"></a>Sottoporre a profilatura applicazioni autonome

|Attività|Contenuti correlati|
|----------|---------------------|
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profilare usando il metodo di strumentazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Sottoporre a profilatura l'allocazione di memoria .NET e la garbage collection**|-   [Raccogliere dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Aggiungere dati di interazione tra livelli**|-   [Raccogliere dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Sottoporre a profilatura i problemi di concorrenza

|Attività|Contenuti correlati|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni ASP.NET**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Sottoporre a profilatura i servizi**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di concorrenza
- [Visualizzazioni dei dati sui contenuti delle risorse](../profiling/resource-contention-data-views.md)

- [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Riferimento
- [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)
