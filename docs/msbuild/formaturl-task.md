---
title: Attività FormatUrl | Microsoft Docs
description: Informazioni su come usare l'attività FormatUrl di MSBuild per convertire un URL di input in un formato di URL di output corretto.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0e38a0f1aea6999e30d2ab2493873f66cd907878
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436884"
---
# <a name="formaturl-task"></a>FormatUrl task (attività)

Converte un URL in un formato URL corretto.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `FormatUrl` .

|Parametro|Descrizione|
|---------------|-----------------|
|`InputUrl`|Parametro `String` facoltativo.<br /><br /> Specifica l'URL da formattare.|
|`OutputUrl`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica l'URL formattato.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)