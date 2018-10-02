---
title: Attività CPPClean | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9437f72beef4f51568293543fcfaeeee2f65224c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526684"
---
# <a name="cppclean-task"></a>Attività CPPClean
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività CPPClean](https://docs.microsoft.com/visualstudio/msbuild/cppclean-task).  
  
  
Elimina i file temporanei creati da MSBuild al momento della compilazione di un progetto Visual C++. Il processo di eliminazione dei file di compilazione è noto come *pulizia*.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **CPPClean**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**DeletedFiles**|Parametro di ouput facoltativo `ITaskItem[]`.<br /><br /> Definisce una matrice di elementi del file di output MSBuild che può essere usata ed emessa dalle attività.|  
|**DoDelete**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, vengono puliti i file di compilazione temporanei.|  
|**FilePatternsToDeleteOnClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle estensioni dei file di cui eseguire la pulizia.|  
|**FilesExcludedFromClean**|Parametro `String` facoltativo.<br /><br /> Specifica un elenco delimitato da punto e virgola dei file di cui non eseguire la pulizia.|  
|**FoldersToClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle directory di cui eseguire la pulizia. È possibile specificare un percorso completo o relativo e il percorso può contenere il carattere jolly (**\***).|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)



