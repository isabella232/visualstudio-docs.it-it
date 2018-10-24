---
title: Attività CPPClean | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: a96571cbc4de4281daddd42f4b1d53b60b300e53
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826947"
---
# <a name="cppclean-task"></a>Attività CPPClean
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Elimina i file temporanei creati da MSBuild al momento della compilazione di un progetto Visual C++. Il processo di eliminazione dei file di compilazione è noto come *pulizia*.  

## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **CPPClean**.  


|            Parametro            |                                                                                                Descrizione                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Parametro di ouput facoltativo `ITaskItem[]`.<br /><br /> Definisce una matrice di elementi del file di output MSBuild che può essere usata ed emessa dalle attività.                                |
|          **DoDelete**           |                                                            Parametro **Boolean** facoltativo.<br /><br /> Se `true`, vengono puliti i file di compilazione temporanei.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle estensioni dei file di cui eseguire la pulizia.                                             |
|   **FilesExcludedFromClean**    |                                                    Parametro `String` facoltativo.<br /><br /> Specifica un elenco delimitato da punto e virgola dei file di cui non eseguire la pulizia.                                                    |
|       **FoldersToClean**        | Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle directory di cui eseguire la pulizia. È possibile specificare un percorso relativo o completo e il percorso può contenere il carattere jolly asterisco (**\\**\*). |

## <a name="remarks"></a>Note  

## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)



