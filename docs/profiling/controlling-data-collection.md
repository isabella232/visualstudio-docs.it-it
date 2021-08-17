---
title: Controllo della raccolta di dati | Microsoft Docs
description: Informazioni su come avviare e arrestare Strumenti di profilatura raccolta dati e come limitare gli oggetti per cui vengono raccolti i dati di profilatura. Questo articolo è una panoramica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bb967ea2e8c3b22428217f05b49a9cb917d16abb80ea6d41cf3e8c0bea10cde3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333483"
---
# <a name="control-data-collection"></a>Controllare la raccolta dati
Gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consentono di controllare quando i dati di profilatura vengono raccolti durante una sessione prestazioni e di specificare le funzioni che vengono profilate. In questa sezione viene descritto come avviare e arrestare la raccolta dei dati dalle finestre **Esplora prestazioni** e **Controllo raccolta dati** e come limitare gli oggetti per i quali vengono raccolti i dati di profilatura.

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Avviare e interrompere la profilatura:** è possibile avviare la profilatura di un'applicazione all'avvio dell'applicazione, oppure collegare il profiler a un processo già in esecuzione. Quando l'applicazione di destinazione è in esecuzione, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura chiudere l'applicazione di destinazione o disconnettere il profiler da un processo in esecuzione.|-   [Procedura: Iniziare e terminare la raccolta dati sulle prestazioni](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Procedura: Connettere e disconnettere gli strumenti per le prestazioni ai processi in esecuzione](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Procedura: Sospendere e riprendere la raccolta dati prestazioni](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Configurare la profilatura della strumentazione per limitare i dati raccolti:** è possibile usare la configurazione della sessione prestazioni per limitare i dati raccolti durante le esecuzioni della profilatura che usano il metodo di strumentazione. È possibile includere o escludere specifici file con estensione dll, spazi dei nomi, classi e funzioni. È anche possibile escludere le funzioni che non soddisfano una soglia di dimensioni specificata.|-   [Procedura: Limitare la strumentazione a specifiche DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Procedura: Limitare la strumentazione a funzioni specifiche](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Procedura: Escludere o includere funzioni brevi dalla strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Sezioni correlate
- [Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Vedi anche
- [Esplora prestazioni](../profiling/performance-explorer.md)
