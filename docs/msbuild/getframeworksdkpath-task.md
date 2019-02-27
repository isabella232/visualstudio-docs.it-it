---
title: Attività GetFrameworkSdkPath | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15346bdd7c049a152a5a2d1668891f9d97da31fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644354"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath (attività)
Recupera il percorso di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].

## <a name="task-parameters"></a>Parametri dell'attività
Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkSdkPath` .

|Parametro|Description|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 2.0, se presente. In caso contrario restituisce `String.Empty`.|
|`FrameworkSdkVersion35Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 3.5, se presente. In caso contrario restituisce `String.Empty`.|
|`FrameworkSdkVersion40Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 4.0, se presente. In caso contrario restituisce `String.Empty`.|
|`Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso della versione più recente di .NET SDK, se sono presenti delle versioni. In caso contrario restituisce `String.Empty`.|

## <a name="remarks"></a>Osservazioni
Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio
Nell'esempio seguente viene usata l'attività `GetFrameworkSdkPath` per archiviare il percorso a [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] nella proprietà `SdkPath`.

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
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
