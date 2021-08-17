---
title: Attività GetAssemblyIdentity | Microsoft Docs
description: Usare l MSBuild'attività GetAssemblyIdentity per recuperare le identità dell'assembly dai file specificati e ottenere le informazioni sull'identità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b016d39453e79aea045c61a84202cad71d4164c32bc5d0aa566dd27f49870b77
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427814"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity (attività)

Recupera le identità degli assembly dai file specificati ed estrae le informazioni sulle identità.

## <a name="task-parameters"></a>Parametri dell'attività

Nella tabella che segue vengono descritti i parametri dell'attività `GetAssemblyIdentity` .

|Parametro|Descrizione|
|---------------|-----------------|
|`Assemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene le identità di assembly recuperate.|
|`AssemblyFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da cui recuperare le identità.|

## <a name="remarks"></a>Commenti

Gli elementi estratti dal parametro `Assemblies` contengono voci di metadati degli elementi denominati `Version`, `PublicKeyToken` e `Culture`.

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Esempio

Nell'esempio seguente l'identità dei file specificati nell'elemento `MyAssemblies` viene recuperata ed estratta nell'elemento `MyAssemblyIdentities`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
