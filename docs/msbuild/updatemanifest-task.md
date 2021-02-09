---
title: Attività UpdateManifest | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività UpdateManifest per aggiornare le proprietà selezionate in un manifesto e rifirmarle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8bb090b66a52e9c2931e8bf4afc878d87a0ae36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902497"
---
# <a name="updatemanifest-task"></a>Attività UpdateManifest

Aggiorna le proprietà selezionate in un manifesto e ripete la firma.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `UpdateManifest` .

|Parametro|Descrizione|
|---------------|-----------------|
|`ApplicationManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il manifesto dell'applicazione.|
|`ApplicationPath`|Parametro `String` obbligatorio.<br /><br /> Specifica il percorso del manifesto dell'applicazione.|
|`InputManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il manifesto da aggiornare.|
|`OutputManifest`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il manifesto che contiene le proprietà aggiornate.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)