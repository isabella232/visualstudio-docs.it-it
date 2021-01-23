---
title: Informazioni sui metodi di raccolta delle prestazioni del profiler
description: Informazioni sui metodi di raccolta dei dati usati dagli strumenti all'interno del profiler delle prestazioni di Visual Studio.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: e34fd78d7ff44aeffc4ca4d61c84a0a9af6747a5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722269"
---
# <a name="understand-profiler-performance-collection-methods"></a>Informazioni sui metodi di raccolta delle prestazioni del profiler

Questo documento illustra i metodi di raccolta dei dati usati dagli strumenti all'interno del profiler delle prestazioni di Visual Studio. 

## <a name="sampling"></a>campionamento

Metodi di campionamento per la profilatura raccogliere dati statistici sul lavoro eseguito da un'applicazione durante un'esecuzione della profilatura. La raccolta dei dati viene eseguita raccogliendo informazioni sull'applicazione a intervalli regolari o frequenza di campionamento, ad esempio ogni millisecondo e quindi analizzando questi dati per creare un modello in cui è stato impiegato il tempo nell'applicazione. Il metodo di campionamento è leggero e ha un effetto minimo sull'esecuzione dell'applicazione profilata. Gli strumenti nel profiler delle prestazioni che utilizzano il metodo di campionamento includono lo strumento [utilizzo CPU](../profiling/cpu-usage.md) .

## <a name="instrumentation"></a>Strumentazione

La profilatura della strumentazione raccoglie informazioni dettagliate sul lavoro eseguito da un'applicazione durante un'esecuzione della profilatura. La raccolta dei dati viene eseguita da strumenti che inseriscono codice in un file binario che acquisisce informazioni sull'intervallo o usando hook di callback per raccogliere ed emettere le informazioni esatte sulla tempistica e sul conteggio delle chiamate durante l'esecuzione di un'applicazione. Il metodo di strumentazione presenta un sovraccarico elevato rispetto agli approcci basati sul campionamento. Gli strumenti nel profiler delle prestazioni che usano la strumentazione includono lo strumento di [allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md) .