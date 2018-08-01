---
title: Attività CPPClean | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 749d60c764f522d188b45b4ecf7302d69b6cd64b
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179079"
---
# <a name="cppclean-task"></a>Attività CPPClean
Elimina i file temporanei creati da MSBuild al momento della compilazione di un progetto Visual C++. Il processo di eliminazione dei file di compilazione è noto come *pulizia*.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **CPPClean**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**DeletedFiles**|Parametro di ouput facoltativo `ITaskItem[]`.<br /><br /> Definisce una matrice di elementi del file di output MSBuild che può essere usata ed emessa dalle attività.|  
|**DoDelete**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, vengono puliti i file di compilazione temporanei.|  
|**FilePatternsToDeleteOnClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle estensioni dei file di cui eseguire la pulizia.|  
|**FilesExcludedFromClean**|Parametro `String` facoltativo.<br /><br /> Specifica un elenco delimitato da punto e virgola dei file di cui non eseguire la pulizia.|  
|**FoldersToClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle directory di cui eseguire la pulizia. È possibile specificare un percorso completo o relativo. Il percorso può contenere il carattere jolly (*).|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)