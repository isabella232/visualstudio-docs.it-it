---
title: Using Memory Efficiently When You Build Large Projects (Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni) | Microsoft Docs
description: Informazioni su MSBuild la memoria automaticamente, ad esempio lo scaricamento di versioni precedenti e il recupero di cache, durante la compilazione di progetti di grandi dimensioni.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 18e1cf21168a25bdc25ba0556ef62aa681fc0ad001b4c448631fe637d03cc7c8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369488"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni

I progetti di grandi dimensioni spesso contengono molti sottoprogetti e altre dipendenze, che possono utilizzare una grande quantità di memoria di sistema in fase di compilazione. Quando viene ridotta la memoria di sistema disponibile, le prestazioni del sistema possono anche essere ridotte. Le versioni precedenti MSBuild progetti sono rimasti in memoria. La versione 3.5 rimuoveva le versioni precedenti dei progetti, ma manteneva i risultati delle compilazioni in una cache per un recupero successivo.

 La versione 4.0 gestisce automaticamente la memoria, evitando che i progetti debbano usare proprietà come `UnloadProjectsOnCompletion` e `UseResultsCache`.

### <a name="see-also"></a>Vedi anche

- [Compilare più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
