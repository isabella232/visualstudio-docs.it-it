---
title: Attività GetFrameworkSdkPath | Microsoft Docs
description: Informazioni su come usare l'MSBuild GetFrameworkSdkPath per recuperare il percorso dell'SDK Windows.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c785e7d7e12a77650f607fc58798f6b80b73f0f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093814"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath (attività)

Recupera il percorso del Windows Software Development Kit (SDK).
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

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene `GetFrameworkSdkPath` utilizzata l'attività per archiviare il percorso Windows SDK nella `SdkPath` proprietà .

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

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
