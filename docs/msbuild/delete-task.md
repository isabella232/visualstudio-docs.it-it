---
title: Attività Delete | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eddb9804378a4c32de9d1b68f952bc715f32ffd6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288910"
---
# <a name="delete-task"></a>Delete (attività)

Elimina i file specificati.

## <a name="parameters"></a>Parametri

Nella tabella che segue vengono descritti i parametri dell'attività `Delete` .

|Parametro|Description|
|---------------|-----------------|
|`DeletedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file che sono stati eliminati correttamente.|
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da eliminare.|
|`TreatErrorsAsWarnings`|Parametro `Boolean` facoltativo<br /><br /> Se `true`, gli errori vengono registrati come avvisi. Il valore predefinito è `false`.|

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Prestare attenzione quando si usano caratteri jolly con l' `Delete` attività. È possibile eliminare facilmente i file non corretti con espressioni come `$(SomeProperty)\**\*.*` o `$(SomeProperty)/**/*.*` , soprattutto se la proprietà restituisce una stringa vuota, nel qual caso il `Files` parametro può restituire la radice dell'unità ed eliminare molto più di quanto si vuole eliminare.

## <a name="example"></a>Esempio

Nell'esempio seguente viene eliminato il file *MyApp. pdb* quando si compila la `DeleteDebugSymbolFile` destinazione.

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

Se è necessario tenere traccia dei file eliminati, impostare `TaskParameter` su `DeletedFiles` con il nome dell'elemento, come indicato di seguito:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Anziché utilizzare direttamente caratteri jolly nell' `Delete` attività, creare un `ItemGroup` di file da eliminare ed eseguire l' `Delete` attività. Tuttavia, assicurarsi di inserire `ItemGroup` attentamente. Se si inserisce un oggetto `ItemGroup` al primo livello in un file di progetto, questo viene valutato in anticipo, prima dell'avvio della compilazione, in modo che non includa i file compilati come parte del processo di compilazione. Quindi, inserire l'oggetto `ItemGroup` che crea l'elenco di elementi da eliminare in una destinazione vicina all' `Delete` attività. È anche possibile specificare una condizione per verificare che la proprietà non sia vuota, in modo che non venga creato un elenco di elementi con un percorso che inizia dalla radice dell'unità.

L' `Delete` attività è destinata all'eliminazione di file. Se si desidera eliminare una directory, utilizzare [RemoveDir](removedir-task.md).

L' `Delete` attività non fornisce un'opzione per eliminare i file di sola lettura. Per eliminare i file di sola lettura, è possibile usare l' `Exec` attività per eseguire il `del` comando o l'equivalente, con l'opzione appropriata per abilitare l'eliminazione dei file di sola lettura. È necessario prestare attenzione alla lunghezza dell'elenco di elementi di input, dal momento che la riga di comando presenta una limitazione di lunghezza, oltre a garantire la gestione dei nomi di file con spazi, come in questo esempio:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

In generale, quando si scrivono script di compilazione, valutare se l'eliminazione è logicamente parte di un' `Clean` operazione. Se è necessario impostare alcuni file da pulire come parte di un' `Clean` operazione normale, è possibile aggiungerli all' `@(FileWrites)` elenco e verranno eliminati al successivo `Clean` . Se è necessaria una maggiore elaborazione personalizzata, definire una destinazione e specificarne l'esecuzione impostando l'attributo `BeforeTargets="Clean"` o oppure `AfterTargets="Clean"` definire la versione personalizzata delle `BeforeClean` `AfterClean` destinazioni o. Vedere [personalizzare la compilazione](customize-your-build.md).

## <a name="see-also"></a>Vedi anche

- [RemoveDir (attività)](removedir-task.md)
- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
