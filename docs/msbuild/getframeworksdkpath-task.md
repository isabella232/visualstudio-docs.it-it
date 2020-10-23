---
title: Attività GetFrameworkSdkPath | Microsoft Docs
description: Informazioni su come usare l'attività GetFrameworkSdkPath di MSBuild per recuperare il percorso del Windows SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4061dbe96c84648aacf136c0d59b92a2af037e2
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436816"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath (attività)

Recupera il percorso di Windows Software Development Kit (SDK).
## <a name="task-parameters"></a>Parametri dell'attività

Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkSdkPath` .
Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkSdkPath` .

|Parametro|Descrizione|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 2.0, se presente. In caso contrario restituisce `String.Empty`.|
|`FrameworkSdkVersion35Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 3.5, se presente. In caso contrario restituisce `String.Empty`.|
|`FrameworkSdkVersion40Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 4.0, se presente. In caso contrario restituisce `String.Empty`.|
|`Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso della versione più recente di .NET SDK, se sono presenti delle versioni. In caso contrario restituisce `String.Empty`.|

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene utilizzata l' `GetFrameworkSdkPath` attività per archiviare il percorso del Windows SDK nella `SdkPath` Proprietà.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
