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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 250c73ce0395f278b72c18605f1666290670e20a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634110"
---
# <a name="formatversion-task"></a>Attività FormatVersion

Aggiunge il numero di revisione al numero di versione.

- Caso n. 1: Input: Version=\<indefinita>;  Revision=\<indifferente>;   Output: OutputVersion="1.0.0.0"

- Caso n. 2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"

- Caso n. 3: Input: Version="1.0.0.0"  Revision=\<indifferente>;  Output: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `FormatVersion`.

|Parametro|Descrizione|
|---------------|-----------------|
|`FormatType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di formato.<br /><br /> -   "Version" = versione.<br />-   "Path" = sostituire "." con "_";|
|`OutputVersion`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la versione di output che include il numero di revisione.|
|`Revision`|Parametro `Int32` facoltativo.<br /><br /> Specifica la revisione da accodare alla versione.|
|`Version`|Parametro `String` facoltativo.<br /><br /> Specifica la stringa del numero di versione da formattare.|

## <a name="remarks"></a>Note

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
