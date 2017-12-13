---
title: Using Memory Efficiently When You Build Large Projects (Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e9484e0b8771ad665f1891298ff2f6a8a1d0005e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Utilizzo efficiente della memoria nella compilazione di progetti di grandi dimensioni
I progetti di grandi dimensioni spesso contengono molti sottoprogetti e altre dipendenze che possono consumare una grande quantità di memoria di sistema in fase di compilazione. Quando viene ridotta la memoria di sistema disponibile, le prestazioni del sistema possono anche essere ridotte. Le versioni precedenti di progetti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sono rimaste in memoria o, nella versione 3.5 i progetti sono stati rimossi, ma risultati della compilazione sono conservati in una cache per il successivo recupero.  
  
 La versione 4.0 gestisce automaticamente la memoria, evitando che i progetti debbano usare proprietà come `UnloadProjectsOnCompletion` e `UseResultsCache`.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)