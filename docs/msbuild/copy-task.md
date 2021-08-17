---
title: Attività Copy | Microsoft Docs
description: Informazioni su come usare l'MSBuild copia per copiare file in un nuovo percorso di file o cartella nel file system.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f8bcaf1e13a9b6f26d3c838c8cbd739d91c99d62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054990"
---
# <a name="copy-task"></a>Copy (attività)

Copia i file in un nuovo percorso del file system.

## <a name="parameters"></a>Parametri

Nella tabella che segue vengono descritti i parametri dell'attività `Copy` .

|Parametro|Descrizione|
|---------------|-----------------|
|`CopiedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi copiati *correttamente,* inclusi quelli che non sono stati effettivamente copiati, ma sono stati ignorati perché erano già aggiornati ed `SkipUnchangedFiles` era `true` .|
|`DestinationFiles`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica l'elenco di file in cui copiare i file di origine. Dovrebbe esistere un mapping uno-a-uno tra questo elenco e quello specificato nel parametro `SourceFiles`. In altri termini, il primo file specificato in `SourceFiles` verrà copiato nel primo percorso specificato in `DestinationFiles`e così via.|
|`DestinationFolder`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la directory in cui si vogliono copiare i file. Deve trattarsi di una directory, non di un file. Se la directory non esiste, viene creata automaticamente.|
|`OverwriteReadOnlyFiles`|Parametro `Boolean` facoltativo.<br /><br /> Sovrascrivi file anche se sono contrassegnati come file di sola lettura|
|`Retries`|Parametro `Int32` facoltativo.<br /><br /> Specifica il numero di tentativi da eseguire per la copia, se tutti i tentativi precedenti hanno avuto esito negativo. Il valore predefinito è zero.<br /><br /> **Attenzione:** L'uso di tentativi può mascherare un problema di sincronizzazione nel processo di compilazione.<br /><br /> **Nota:** Mentre *l'impostazione* predefinita dell'attività è zero tentativi, gli utilizzi dell'attività spesso `$(CopyRetryCount)` passano, che è diverso da zero per impostazione predefinita.|
|`RetryDelayMilliseconds`|Parametro `Int32` facoltativo.<br /><br /> Specifica il ritardo tra eventuali nuovi tentativi necessari. Imposta come valore predefinito l'argomento RetryDelayMillisecondsDefault, che viene passato al costruttore CopyTask.|
|`SkipUnchangedFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, i file rimasti invariati dall'origine alla destinazione non vengono copiati. L'attività `Copy` considera invariati i file con le stesse dimensioni e la stessa ora dell'ultima modifica. <br /><br /> **Nota:** Se questo parametro viene impostato su `true`, è consigliabile non usare l'analisi delle dipendenze nella destinazione contenitore, perché in questo caso l'attività viene eseguita soltanto se l'ora dell'ultima modifica dei file di origine è più recente rispetto a quella dei file di destinazione.|
|`SourceFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da copiare.|
|`UseHardlinksIfPossible`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, vengono creati dei collegamenti reali per i file copiati invece di copiare i file.|

## <a name="warnings"></a>Avvisi

Gli avvisi vengono registrati, inclusi:

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>Commenti

È necessario specificare il parametro `DestinationFolder` o `DestinationFiles`, ma non entrambi. Se vengono specificati entrambi, l'attività avrà esito negativo e verrà registrato un errore.

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example-1"></a>Esempio 1

Nell'esempio riportato di seguito gli elementi della raccolta `MySourceFiles` vengono copiati nella cartella *c:\MyProject\Destination*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFolder="c:\MyProject\Destination"
        />
    </Target>

</Project>
```

## <a name="example-2"></a>Esempio 2

Nell'esempio riportato di seguito viene illustrato come creare una copia ricorsiva. Tutti i file del progetto vengono copiati in modo ricorsivo da *c:\MySourceTree* a *c:\MyDestinationTree*, mantenendo al tempo stesso la struttura di directory.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
