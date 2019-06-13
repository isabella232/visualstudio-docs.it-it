---
title: Attività GetFrameworkPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d7bf2432e37278c924d1604e735feec7b848b01
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747549"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath (attività)
Recupera il percorso agli assembly .NET Framework.

## <a name="task-parameters"></a>Parametri dell'attività
Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkPath` .

|Parametro|Description|
|---------------|-----------------|
|`FrameworkVersion11Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 1.1 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion20Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 2.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion30Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion35Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.5 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion40Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 4.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly del framework più recente, se disponibili. In caso contrario restituisce `null`.|

## <a name="remarks"></a>Osservazioni
Se sono installate più versioni di .NET Framework, questa operazione restituisce la versione che [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è progettato per l'esecuzione.

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio
L'esempio seguente usa il `GetFrameworkPath` attività per archiviare il percorso di .NET Framework nel `FrameworkPath` proprietà.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
