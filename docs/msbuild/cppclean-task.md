---
title: Attività CPPClean | Microsoft Docs
ms.date: 11/04/2016
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
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 331a96c7cd67b933e521e3fe5f2d7a909ffa5d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634344"
---
# <a name="cppclean-task"></a>Attività CPPClean

Elimina i file temporanei creati da MSBuild quando viene compilato un progetto in c'è. Il processo di eliminazione dei file di compilazione è noto come *pulizia*.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività **CPPClean**.

|Parametro|Descrizione|
|---------------|-----------------|
|**DeletedFiles**|Parametro di ouput facoltativo `ITaskItem[]`.<br /><br /> Definisce una matrice di elementi del file di output MSBuild che può essere usata ed emessa dalle attività.|
|**DoDelete**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, vengono puliti i file di compilazione temporanei.|
|**FilePatternsToDeleteOnClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle estensioni dei file di cui eseguire la pulizia.|
|**FilesExcludedFromClean**|Parametro `String` facoltativo.<br /><br /> Specifica un elenco delimitato da punto e virgola dei file di cui non eseguire la pulizia.|
|**FoldersToClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punto e virgola delle directory di cui eseguire la pulizia. È possibile specificare un percorso completo o relativo. Il percorso può contenere il carattere jolly (*).|

## <a name="see-also"></a>Vedere anche

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
