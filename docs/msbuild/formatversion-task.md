---
title: Attività FormatVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc1651ae769a9dbe8ef8fbd9b8a1a50dd83ea0f6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640714"
---
# <a name="formatversion-task"></a>Attività FormatVersion
Aggiunge il numero di revisione al numero di versione.

-   Caso n. 1: Input: Version=\<indefinita>;  Revision=\<indifferente>;   Output: OutputVersion="1.0.0.0"

-   Caso n. 2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"

-   Caso n. 3: Input: Version="1.0.0.0"  Revision=\<indifferente>;  Output: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parametri
 Nella tabella che segue vengono descritti i parametri dell'attività `FormatVersion` .

|Parametro|Description|
|---------------|-----------------|
|`FormatType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di formato.<br /><br /> -   "Version" = versione.<br />-   "Path" = sostituire "." con "_";|
|`OutputVersion`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la versione di output che include il numero di revisione.|
|`Revision`|Parametro `Int32` facoltativo.<br /><br /> Specifica la revisione da accodare alla versione.|
|`Version`|Parametro `String` facoltativo.<br /><br /> Specifica la stringa del numero di versione da formattare.|

## <a name="remarks"></a>Osservazioni
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)