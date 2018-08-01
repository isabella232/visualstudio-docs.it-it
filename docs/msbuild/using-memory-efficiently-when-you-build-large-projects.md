---
title: Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99550ffd42e5a3cca919ee9dd00658c66ee0e4b0
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178982"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni
I progetti di grandi dimensioni spesso contengono molti sottoprogetti e altre dipendenze, che possono utilizzare una grande quantità di memoria di sistema in fase di compilazione. Quando viene ridotta la memoria di sistema disponibile, le prestazioni del sistema possono anche essere ridotte. Le versioni precedenti di progetti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rimanevano in memoria. La versione 3.5 rimuoveva le versioni precedenti dei progetti, ma manteneva i risultati delle compilazioni in una cache per un recupero successivo.  
  
 La versione 4.0 gestisce automaticamente la memoria, evitando che i progetti debbano usare proprietà come `UnloadProjectsOnCompletion` e `UseResultsCache`.  
  
### <a name="see-also"></a>Vedere anche  
 [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)