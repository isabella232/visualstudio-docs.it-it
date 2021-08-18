---
title: Tabella di riferimento delle regole di prestazioni | Microsoft Docs
description: Informazioni su come le regole per le prestazioni Strumenti di profilatura forniscono avvisi e informazioni aggiuntive sulle prestazioni dell'applicazione.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e22e4831d92bc17d1a0c6ac4463a94f85ead2f00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141636"
---
# <a name="performance-rules-reference"></a>Tabella di riferimento delle regole di prestazioni
Le regole di prestazioni degli strumenti di profilatura forniscono informazioni e avvisi aggiuntivi sulle prestazioni dell'applicazione. Le regole di prestazioni consentono di analizzare in un'esecuzione di profilatura i dati raccolti da origini quali i contatori delle prestazioni dei processori e di Windows. I messaggi relativi alle regole vengono visualizzati nella finestra di output degli errori dell'ambiente di sviluppo integrato di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. I messaggi sono elencati con uno dei livelli di regole seguenti:

|Category|Descrizione|
|-|-|
|**Error (Errore) (Error (Errore)e)**|Poche regole generano messaggi di errore poiché la maggior parte dei problemi di prestazioni non sono effettivamente errori. Un messaggio di errore può indicare un errore nella raccolta dei dati di profilatura.|
|**Avviso**|Gli avvisi indicano un'area dell'applicazione che potenzialmente può dare origine a problemi di prestazioni o che potrebbe essere ottimizzata.|
|**Informazioni**|I messaggi di informazioni indicano che l'analisi di una condizione della regola non ha raggiunto la soglia per generare un messaggio di errore o che le informazioni nel messaggio sono utili ma non indicano un problema di prestazioni.|

## <a name="in-this-section"></a>Contenuto della sezione

[Regole di prestazioni in base all'ID](../profiling/performance-rules-by-id.md)

Le regole di prestazioni degli strumenti di profilatura sono organizzate in quattro categorie:

|Category|Descrizione|
|-|-|
|[.NET Framework Regole per le prestazioni di utilizzo](../profiling/dotnet-framework-usage-performance-rules.md)|Regole che consentono di usare .NET Framework in modo efficiente.|
|[Regole di prestazioni relative a memoria e paging](../profiling/memory-and-paging-performance-rules.md)|Regole che analizzano il comportamento di paging e Managed Memory dell'applicazione.|
|[Strumenti di profilatura di utilizzo](../profiling/profiling-tools-usage-rules.md)|Regole che permettono di usare gli strumenti di profilatura in modo efficiente.|
|[Regole delle prestazioni di monitoraggio delle risorse](../profiling/resource-monitoring-performance-rules.md)|Messaggi di informazioni sull'uso del processore e della memoria in un'esecuzione di profilatura.|
