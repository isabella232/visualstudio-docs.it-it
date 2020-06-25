---
title: Raccogliere statistiche per le app Web ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 8f353f551b3b524cfa49fb2cb638c261dcde660d
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331924"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Raccogliere statistiche per le app Web ASP.NET

Questa sezione descrive le procedure e le opzioni per la raccolta di statistiche sulle prestazioni per un'applicazione Web ASP.NET tramite gli strumenti da riga di comando **VSPerfASPNETCmd** e **VSPerfCmd** e il metodo di profilatura del campionamento.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Anche se lo strumento **VSPerfCmd** consente l'accesso completo alle funzionalità degli strumenti di profilatura che consentono la sospensione e la ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e dai contatori delle prestazioni di Windows, quando queste funzionalità non sono necessarie è consigliabile usare lo strumento da riga di comando **VSPerfASPNETCmd**. Lo strumento da riga di comando **VSPerfASPNETCmd** è il metodo preferito per la profilatura di siti Web ASP.NET tramite il profiler autonomo. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente né riavviare il computer. Per ulteriori informazioni, vedere [profilatura rapida di siti Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Connettere il profiler a un'applicazione ASP.NET**|-   [Procedura: connessione del profiler a un'applicazione Web ASP.NET per raccogliere statistiche dell'applicazione](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Attività correlate

### <a name="profile-aspnet-web-applications"></a>Sottoporre a profilatura applicazioni Web ASP.NET

|Attività|Contenuto correlato|
|----------|---------------------|
|**Profilare usando il metodo di strumentazione**|-   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profilatura dell'allocazione di memoria e garbage collection**|-   [Raccogliere dati di memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Sottoporre a profilatura i conflitti di risorse e le attività dei thread**|-   [Raccogli dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Metodo di campionamento

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni client autonome**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Servizi profili**|-   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analizzare visualizzazioni dati e report di campionamento
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
