---
title: Configurazione di sessioni di prestazioni | Microsoft Docs
description: Informazioni su come configurare il Visual Studio Strumenti di profilatura raccogliere i dati sulle prestazioni desiderati. Questo articolo elenca le attività comuni e fornisce collegamenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 80b6e2f0e4ca08b78fe57d204e64b981183f8649a294bf38d5c7aa6c67e404d9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333574"
---
# <a name="configure-performance-sessions"></a>Configurare le sessioni di prestazioni
Usando gli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile raccogliere un'ampia gamma di dati sulle prestazioni per un numero elevato di tipi di applicazioni. Questa sezione illustra come usare la Creazione guidata sessione di prestazioni e le proprietà della sessione di prestazioni e del file binario di destinazione per configurare Strumenti di profilatura per raccogliere i dati di interesse. Le proprietà di configurazione degli strumenti per la profilatura possono essere usate anche per controllare quanti dati vengono raccolti in un'esecuzione di profilatura. Per altre informazioni, vedere [Controllare la raccolta dati](../profiling/controlling-data-collection.md).

> [!NOTE]
> In molti casi l'uso delle proprietà della Creazione guidata sessione di prestazioni è un metodo efficace per raccogliere dati di profilatura. Per altre informazioni, vedere [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md) e [Introduzione.](../profiling/getting-started-with-performance-tools.md)

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuto correlato |
| - | - |
| **Impostare le opzioni di profilatura di base:** è necessario configurare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] per usare il server dei simboli Microsoft. Ciò consente di avere accesso ai simboli, come ad esempio i nomi di parametri e funzioni, per la versione corrente di Windows e per altre applicazioni Microsoft. È anche possibile specificare altre opzioni generali prima di avviare una sessione di profilatura, ad esempio autorizzazioni di sistema per gli strumenti di profilatura e i nomi dei file di dati di profilatura. | -   [Procedura: Fare riferimento Windows informazioni sui simboli](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Procedura: Serializzare le informazioni sui simboli](../profiling/how-to-serialize-symbol-information.md)<br />-   [Procedura: Impostare la sessione corrente](../profiling/how-to-set-the-current-session.md)<br />-   [Procedura: Impostare le autorizzazioni](../profiling/how-to-set-permissions.md)<br />-   [Procedura: Impostare le opzioni relative al nome del file di dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Specificare i dati che si vuole raccogliere:** le procedure per configurare una sessione di profilatura variano a seconda del tipo di applicazione di destinazione che si vuole profilare e del tipo di dati sulle prestazioni che si vuole raccogliere. | -   [Procedura: Scegliere i metodi di raccolta](../profiling/how-to-choose-collection-methods.md)<br />-   [Raccogliere statistiche sulle prestazioni usando il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Raccogliere dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Raccogliere dati di intervallo dettagliati usando la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Procedura: Profilare il codice JavaScript nelle pagine Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Raccogliere dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Raccogliere dati aggiuntivi sulle prestazioni](../profiling/collecting-additional-performance-data.md) |
| **Impostare le opzioni di configurazione avanzata:** quando si esegue la profilatura delle applicazioni .NET Framework che caricano più versioni di common language runtime (CLR), è possibile specificare di quale versione eseguire la profilatura. Quando in una sessione di prestazioni si hanno più file con estensione exe, è possibile impostare l'ordine di avvio dei file binari. | -   [Procedura: Specificare il runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Procedura: Specificare il file binario da avviare](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>Sezioni correlate
- [Controllare la raccolta dati](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Vedi anche
- [Esplora prestazioni](../profiling/performance-explorer.md)
