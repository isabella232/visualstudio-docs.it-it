---
title: Attività WriteLinesToFile | Microsoft Docs
ms.date: 09/20/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b78ac2347a5143aeb532a4bcc294551430584b4a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630665"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile (attività)

Scrive i percorsi degli elementi specificati nel file di testo indicato.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `WriteLinestoFile`.

|Parametro|Descrizione|
|---------------|-----------------|
|`File`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file in cui scrivere gli elementi.|
|`Lines`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli elementi da scrivere nel file.|
|`Overwrite`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività sovrascrive qualsiasi contenuto esistente nel file.|
|`Encoding`|Parametro `String` facoltativo.<br /><br /> Seleziona la codifica dei caratteri, ad esempio "Unicode".  Vedere anche <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il file di destinazione specificato, se presente, verrà letto prima di confrontarlo con quello che sarebbe stato scritto dall'attività. Se identico, il file non viene scritto su disco e il timestamp viene mantenuto.|

## <a name="remarks"></a>Note

 Se `Overwrite` è `true`, crea un nuovo file, scrive il contenuto nel file e quindi lo chiude. Se il file di destinazione è già esistente, viene sovrascritto. Se `Overwrite` è `false`, accoda il contenuto al file, creando il file di destinazione nel caso in cui non esista.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 L'esempio seguente usa l'attività `WriteLinesToFile` per scrivere i percorsi degli elementi della raccolta di elementi `MyItems` nel file specificato dalla raccolta di elementi `MyTextFile`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
        <MyItems Include="*.cs"/>
    </ItemGroup>

    <Target Name="WriteToFile">
        <WriteLinesToFile
            File="@(MyTextFile)"
            Lines="@(MyItems)"
            Overwrite="true"
            Encoding="Unicode"/>
    </Target>

</Project>
```

In questo esempio si usa una proprietà con nuove righe incorporate per scrivere un file di testo con più righe. Se in una voce in `Lines` sono incorporati caratteri di nuova riga, le nuove righe vengono incluse nel file di output. In questo modo è possibile fare riferimento a proprietà su più righe.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
