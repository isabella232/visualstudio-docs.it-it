---
title: Uso efficiente della memoria nella compilazione di progetti di grandi dimensioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b214ff057125b2921ec853fbee004cbb7d41f9e0
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54792767"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Utilizzo efficiente della memoria nella compilazione di progetti di grandi dimensioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
I progetti di grandi dimensioni spesso contengono molti sottoprogetti e altre dipendenze che possono consumare una grande quantità di memoria di sistema in fase di compilazione. Quando viene ridotta la memoria di sistema disponibile, le prestazioni del sistema possono anche essere ridotte. Le versioni precedenti di progetti [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sono rimaste in memoria o, nella versione 3.5 i progetti sono stati rimossi, ma risultati della compilazione sono conservati in una cache per il successivo recupero.  
  
 La versione 4.0 gestisce automaticamente la memoria, evitando che i progetti debbano usare proprietà come `UnloadProjectsOnCompletion` e `UseResultsCache`.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
