---
title: Attività FormatUrl | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5d5a5d6cbe1f0e39f82d551c8c7933104110f4a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579650"
---
# <a name="formaturl-task"></a>FormatUrl task (attività)
Converte un URL in un formato URL corretto.

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività `FormatUrl`.

|Parametro|Descrizione|
|---------------|-----------------|
|`InputUrl`|Parametro `String` facoltativo.<br /><br /> Specifica l'URL da formattare.|
|`OutputUrl`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica l'URL formattato.|

## <a name="remarks"></a>Note
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)