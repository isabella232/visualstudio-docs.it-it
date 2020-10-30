---
title: Using Memory Efficiently When You Build Large Projects (Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni) | Microsoft Docs
description: Informazioni su come MSBuild gestisce automaticamente la memoria, ad esempio scaricare le versioni precedenti e recuperare le cache, durante la compilazione di progetti di grandi dimensioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61bfa09bf91b49c163e47bbf71c0d192b6950160
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047610"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni

I progetti di grandi dimensioni spesso contengono molti sottoprogetti e altre dipendenze, che possono utilizzare una grande quantità di memoria di sistema in fase di compilazione. Quando viene ridotta la memoria di sistema disponibile, le prestazioni del sistema possono anche essere ridotte. Le versioni precedenti dei progetti MSBuild rimanevano in memoria. La versione 3.5 rimuoveva le versioni precedenti dei progetti, ma manteneva i risultati delle compilazioni in una cache per un recupero successivo.

 La versione 4.0 gestisce automaticamente la memoria, evitando che i progetti debbano usare proprietà come `UnloadProjectsOnCompletion` e `UseResultsCache`.

### <a name="see-also"></a>Vedi anche

- [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
