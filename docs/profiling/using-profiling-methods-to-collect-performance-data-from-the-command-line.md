---
title: Usare i metodi di profilatura da riga di comando per ottenere i dati sulle prestazioni
description: Informazioni su come la scelta Visual Studio Strumenti di profilatura strumenti da riga di comando e opzioni dipende da fattori quali il tipo di applicazione di cui si sta profilando.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: adb738b453ed8f26a59953daa3f1e7096ccdf24b1a8ef47bda19433a1ef4269c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270068"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Usare i metodi di profilatura per raccogliere dati sulle prestazioni dalla riga di comando
La scelta degli strumenti e delle opzioni della riga di comando per gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dipende da fattori come il tipo di applicazione sottoposta a profilatura, il metodo di profilatura da usare e il fatto che l'applicazione di destinazione sia scritta in codice nativo o .NET Framework.

 Questo argomento organizza gli argomenti relativi alle procedure della riga di comando in base al metodo di profilatura scelto.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Usare il metodo di campionamento per raccogliere statistiche sulle prestazioni
 Il metodo di campionamento degli strumenti di profilatura raccoglie dati sulle prestazioni a intervalli specificati durante l'esecuzione di una profilatura. I dati di campionamento forniscono informazioni sui problemi di prestazioni associati alla CPU e rappresentano un metodo efficace per iniziare a esplorare le prestazioni di un'applicazione.

 È possibile avviare il profiler e l'applicazione contemporaneamente oppure collegare il profiler a un'istanza di un'applicazione in esecuzione.

|Attività|Tipo di applicazione di destinazione|
|----------|-----------------------------|
|**Avviare un'applicazione**|-   [Applicazioni autonome](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Connettersi a un processo in esecuzione**|-   [.NET Framework applicazioni autonome](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Applicazioni autonome native](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET applicazioni Web](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servizi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servizi nativi](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Usare il metodo di strumentazione per raccogliere dati di intervallo dettagliati
 Il metodo di strumentazione degli strumenti di profilatura raccoglie dati sulle prestazioni da copie dei file binari dell'applicazione che contengono probe software per registrare le informazioni sulle prestazioni. I dati di strumentazione vengono raccolti all'inizio e alla fine di ogni funzione instrumentata e a ogni chiamata ad altre funzioni dalla funzione instrumentata. Il metodo di strumentazione è utile per l'individuazione dei problemi di prestazioni relativi alle attività di I/O, ad esempio l'uso del disco.

 Creare il file binario instrumentato con lo strumento [VInstr.exe](../profiling/vsinstr.md). Dopo l'inizializzazione del profiler, i dati vengono raccolti automaticamente dai file binari instrumentati quando si esegue l'applicazione di destinazione.

 **Tipo di applicazione di destinazione**

- [.NET Framework componenti autonomi](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Componenti autonomi nativi](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Applicazioni Web ASP.NET compilate in modo statico](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Applicazioni Web ASP.NET compilate in modo dinamico](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [Servizi .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Servizi nativi](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Usare i metodi di memoria .NET per raccogliere dati sulla durata degli oggetti e sull'allocazione di memoria
 Il metodo di memoria .NET degli strumenti di profilatura consente di raccogliere dati sull'allocazione di memoria di .NET Framework e informazioni sulla durata degli oggetti in .NET Framework.

 È possibile avviare l'applicazione di destinazione tramite il profiler, collegare il profiler a un'istanza di un'applicazione in esecuzione e creare versioni instrumentate dell'applicazione per raccogliere informazioni dettagliate sugli intervalli insieme ai dati sulla memoria di .NET Framework.

|Attività|Tipo di applicazione di destinazione|
|----------|-----------------------------|
|**Avviare un'applicazione**|-   [Applicazioni .NET Framework autonome](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Connettersi a un processo in esecuzione**|-   [.NET Framework applicazioni autonome](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET applicazioni Web](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Servizi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentare moduli**|-   [.NET Framework componenti autonomi](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Applicazioni Web ASP.NET compilate in modo statico](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Applicazioni Web ASP.NET compilate in modo dinamico](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Servizi .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Usare il metodo di concorrenza per raccogliere dati su attività dei thread e conflitti delle risorse
 Il metodo di concorrenza degli strumenti di profilatura consente di raccogliere informazioni sui conflitti di risorse e dati sull'attività di thread e processi da applicazioni multithread.

 È possibile avviare l'applicazione tramite il profiler oppure collegare il profiler a un'istanza di un'applicazione in esecuzione.

|Attività|Tipo di applicazione di destinazione|
|----------|-----------------------------|
|**Avviare un'applicazione**|-   [Applicazione .NET Framework autonoma](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Applicazione nativa autonoma](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Connettersi a un processo in esecuzione**|-   [.NET Framework'applicazione autonoma](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Applicazione autonoma nativa](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET'applicazione Web](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servizio .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servizio nativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Aggiungere dati di interazione tra livelli a un'esecuzione di profilatura
 L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere Raccogliere [dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
