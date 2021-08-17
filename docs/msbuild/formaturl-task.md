---
title: Attività FormatUrl | Microsoft Docs
description: Informazioni su come usare l'attività FormatUrl MSBuild per convertire un URL di input in un formato di URL di output corretto.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 601adcb918be3efad897ff1a1479b1613e56336fc5582b6d5dc1e2ad1d2e99fb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427899"
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

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)