---
title: "Riga di comando del profiler: ottenere ASP.NET dati di memoria dell'app Web"
description: Informazioni su come usare lo strumento da riga di comando VSPerfCmd per raccogliere l'allocazione di memoria e la data di durata degli oggetti per un'ASP.NET Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: b8cf73fda68447f1d64ba6a597e9bbab47c9011b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076841"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Raccogliere dati di memoria da un'applicazione Web ASP.NET tramite la riga di comando del profiler
In questa sezione vengono descritte le procedure e le opzioni per la raccolta dei dati sull'allocazione di memoria e sulla durata degli oggetti per un'applicazione Web ASP.NET tramite lo strumento da riga di comando **VSPerfCmd.**

> [!NOTE]
> Lo strumento **VSPerfCmd** consente l'accesso completo alle funzionalità degli strumenti di profilatura, tra cui la sospensione e la ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e dai contatori delle prestazioni di Windows. Quando queste funzionalità non sono necessarie è anche possibile usare lo strumento da riga di comando **VSPerfASPNETCmd**. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente né riavviare il computer. Per altre informazioni, vedere [Profilatura rapida del sito Web con VSPerfASPNETCmd.](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Connettere il profiler a un'applicazione ASP.NET in esecuzione**|-   [Procedura: Connettere il profiler a un'ASP.NET Web per raccogliere dati di memoria](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentare file binari compilati in modo statico**|-   [Procedura: Instrumentare un'applicazione ASP.NET compilata in modo statico e raccogliere dati di memoria](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumentare file binari compilati in modo dinamico**|-   [Procedura: Instrumentare un'applicazione ASP.NET dinamica e raccogliere dati di memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-aspnet-web-applications"></a>Sottoporre a profilatura applicazioni Web ASP.NET

|Attività|Contenuto correlato|
|----------|---------------------|
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilare usando il metodo di strumentazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Sottoporre a profilatura i dati di memoria .NET Framework

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccogliere dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Sottoporre a profilatura i servizi**|-   [Raccogliere dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di memoria .NET
- [Viste dati di memoria .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Riferimento
- [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)
