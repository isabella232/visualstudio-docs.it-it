---
title: Attività Delete | Microsoft Docs
description: Informazioni sui parametri e sulle considerazioni sull'uso dell'MSBuild di eliminazione per eliminare i file specificati.
ms.custom: SEO-VS-2020
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09945306a2260bed5b264d380dcea745ff3f7c07
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280423"
---
# <a name="delete-task"></a>Delete (attività)

Elimina i file specificati.

## <a name="parameters"></a>Parametri

Nella tabella che segue vengono descritti i parametri dell'attività `Delete` .

|Parametro|Descrizione|
|---------------|-----------------|
|`DeletedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file che sono stati eliminati correttamente.|
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da eliminare.|
|`TreatErrorsAsWarnings`|Parametro `Boolean` facoltativo<br /><br /> Se `true`, gli errori vengono registrati come avvisi. Il valore predefinito è `false`.|

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Prestare attenzione quando si usano caratteri jolly con `Delete` l'attività . È possibile eliminare facilmente i file erri con espressioni come o , soprattutto se la proprietà restituisce una stringa vuota, nel qual caso il parametro può restituire la radice dell'unità ed eliminare molto di più di quanto si desidera `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*` `Files` eliminare.

## <a name="example"></a>Esempio

L'esempio seguente elimina il file *ConsoleApp1.pdb* quando si compila la `DeleteDebugSymbolFile` destinazione.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Se è necessario tenere traccia dei file eliminati, impostare `TaskParameter` su con il nome `DeletedFiles` dell'elemento, come indicato di seguito:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Anziché usare direttamente i caratteri jolly nell'attività, creare un di file per eliminare `Delete` `ItemGroup` ed eseguire `Delete` l'attività. Tuttavia, assicurarsi di posizionare l'oggetto `ItemGroup` con attenzione. Se si mette un oggetto al primo livello in un file di progetto, viene valutato in anticipo, prima dell'avvio della compilazione, in modo che non includa i file compilati come parte del processo `ItemGroup` di compilazione. Inserire quindi `ItemGroup` l'oggetto che crea l'elenco di elementi da eliminare in una destinazione vicina `Delete` all'attività. È anche possibile specificare una condizione per verificare che la proprietà non sia vuota, in modo che non si crei un elenco di elementi con un percorso che inizia nella radice dell'unità.

`Delete`L'attività è destinata all'eliminazione di file. Se si vuole eliminare una directory, usare [RemoveDir](removedir-task.md).

`Delete`L'attività non offre un'opzione per eliminare i file di sola lettura. Per eliminare file di sola lettura, è possibile usare l'attività per eseguire il comando o equivalente, con l'opzione appropriata per abilitare `Exec` l'eliminazione di file di sola `del` lettura. È necessario prestare attenzione alla lunghezza dell'elenco di elementi di input, poiché esiste una limitazione di lunghezza nella riga di comando, nonché assicurarsi di gestire i nomi file con spazi, come in questo esempio:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

In generale, quando si scrivono script di compilazione, valutare se l'eliminazione fa logicamente parte di `Clean` un'operazione. Se è necessario impostare alcuni file da pulire come parte di un'operazione normale, è possibile aggiungerli all'elenco e verranno eliminati nel `Clean` `@(FileWrites)` successivo `Clean` . Se è necessaria un'elaborazione più personalizzata, definire una destinazione e specificarne l'esecuzione impostando l'attributo o oppure definire la `BeforeTargets="Clean"` versione personalizzata delle destinazioni o `AfterTargets="Clean"` `BeforeClean` `AfterClean` . Vedere [Personalizzare la compilazione.](customize-your-build.md)

## <a name="see-also"></a>Vedere anche

- [RemoveDir (attività)](removedir-task.md)
- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
