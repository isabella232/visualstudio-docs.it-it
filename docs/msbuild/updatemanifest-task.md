---
title: Attività UpdateManifest | Microsoft Docs
description: Informazioni su MSBuild'attività UpdateManifest per aggiornare le proprietà selezionate in un manifesto e dimettersi.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e180eae1f2221b4450584d24a0daaf049c4c3480fe5b90bc37d8f06362b4b54e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369540"
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

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base attività](../msbuild/task-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)