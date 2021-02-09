---
title: Attività FormatVersion | Microsoft Docs
description: Informazioni sui vari modi in cui le attività FormatVersion di MSBuild aggiungono il numero di revisione al numero di versione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6444811750a59de5488b8ca3614f9926d472746
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905478"
---
# <a name="formatversion-task"></a>Attività FormatVersion

Aggiunge il numero di revisione al numero di versione.

- Case #1: input: Version = \<undefined> ;  Revisione = \<don't care> ;   Output: OutputVersion = "1.0.0.0"

- Caso n. 2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"

- Case #3: input: Version = "1.0.0.0" Revision = \<don't care> ;  Output: OutputVersion = "1.0.0.0"

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `FormatVersion` .

|Parametro|Descrizione|
|---------------|-----------------|
|`FormatType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di formato.<br /><br /> -   "Version" = versione.<br />-   "Path" = sostituire "." con "_";|
|`OutputVersion`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la versione di output che include il numero di revisione.|
|`Revision`|Parametro `Int32` facoltativo.<br /><br /> Specifica la revisione da accodare alla versione.|
|`Version`|Parametro `String` facoltativo.<br /><br /> Specifica la stringa del numero di versione da formattare.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
