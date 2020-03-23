---
title: Ottenere dati sulla memoria delle app Web ASP.NET tramite la riga di comando del profiler
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 9e8d9fde00a2390793ae8efe05b684e73caca321
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773059"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Raccogliere dati di memoria da un'applicazione Web ASP.NET tramite la riga di comando del profiler
Questa sezione descrive le procedure e le opzioni per la raccolta di dati sull'allocazione della memoria e sulla durata degli oggetti per un'applicazione Web ASP.NET tramite lo strumento da riga di comando **VSPerfCmd**.

> [!NOTE]
> Lo strumento **VSPerfCmd** consente l'accesso completo alle funzionalità degli strumenti di profilatura, tra cui la sospensione e la ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e dai contatori delle prestazioni di Windows. Quando queste funzionalità non sono necessarie è anche possibile usare lo strumento da riga di comando **VSPerfASPNETCmd**. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente né riavviare il computer. Per ulteriori informazioni, vedere [Profiling di siti Web rapid con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Connettere il profiler a un'applicazione ASP.NET in esecuzione**|-   [Procedura: collegare il profiler a un'applicazione Web ASP.NET per raccogliere dati di memoriaHow to: Attach the profiler to an ASP.NET web application to collect memory data](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentare file binari compilati in modo statico**|-   [Procedura: instrumentare un'applicazione ASP.NET compilata in modo statico e raccogliere dati di memoriaHow to: Instrument a statically compiled ASP.NET application and collect memory data](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumentare file binari compilati in modo dinamico**|-   [Procedura: instrumentare un'applicazione ASP.NET compilata in modo dinamico e raccogliere dati di memoriaHow to: Instrument a dynamically compiled ASP.NET application and collect memory data](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-aspnet-web-applications"></a>Sottoporre a profilatura applicazioni Web ASP.NET

|Attività|Contenuto correlato|
|----------|---------------------|
|**Eseguire la profilatura tramite il metodo di campionamento**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profilare usando il metodo di strumentazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccogliere dati di concorrenzaCollect concurrency data](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Sottoporre a profilatura i dati di memoria .NET Framework

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccogliere dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Sottoporre a profilatura i servizi**|-   [Raccogliere dati di memoria .NETCollect .NET memory data](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di memoria .NET
- [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Informazioni di riferimento
- [Informazioni di riferimento sulle strumenti di profilatura della riga di comandoCommand-line profiling tools reference](../profiling/command-line-profiling-tools-reference.md)
