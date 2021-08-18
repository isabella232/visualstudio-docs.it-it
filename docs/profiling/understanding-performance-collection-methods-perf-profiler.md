---
title: Informazioni su metodi di raccolta delle prestazioni del profiler
description: Informazioni sui metodi di raccolta dei dati che gli strumenti all'interno Visual Studio Profiler prestazioni utilizzare.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 8ca31215b5b9d27725f6feaa5ba65f91ebc119ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156955"
---
# <a name="understand-profiler-performance-collection-methods"></a>Informazioni su metodi di raccolta delle prestazioni del profiler

Questo documento illustra i metodi di raccolta dei dati che gli strumenti all'interno Visual Studio Profiler prestazioni utilizzare. 

## <a name="sampling"></a>campionamento

I metodi di campionamento per la profilatura raccolgono dati statistici sul lavoro eseguito da un'applicazione durante un'esecuzione della profilatura. La raccolta dei dati viene eseguita raccogliendo informazioni sull'applicazione a intervalli regolari o frequenza di campionamento, ad esempio ogni millisecondo, e quindi analizzando questi dati per creare un modello di dove è stato impiegato il tempo nell'applicazione. Il metodo di campionamento è leggero e non ha alcun effetto sull'esecuzione dell'applicazione profilata. Gli strumenti nel Profiler prestazioni che utilizzano il metodo di campionamento includono lo [strumento Utilizzo CPU.](../profiling/cpu-usage.md)

## <a name="instrumentation"></a>Strumentazione

La profilatura della strumentazione raccoglie informazioni dettagliate sul lavoro eseguito da un'applicazione durante un'esecuzione della profilatura. La raccolta dei dati viene eseguita da strumenti che inseriscono codice in un file binario che acquisisce informazioni di intervallo o tramite hook di callback per raccogliere ed generare informazioni esatte sul tempo e sul conteggio delle chiamate durante l'esecuzione di un'applicazione. Il metodo di strumentazione presenta un sovraccarico elevato rispetto agli approcci basati sul campionamento. Gli strumenti nel Profiler prestazioni che usano la strumentazione includono lo strumento di allocazione di oggetti [.NET.](../profiling/dotnet-alloc-tool.md)