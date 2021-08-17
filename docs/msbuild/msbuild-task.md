---
title: Attività MSBuild | Microsoft Docs
description: Informazioni su come l'MSBuild usa lo stesso processo MSBuild per compilare progetti figlio da un altro MSBuild progetto.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 97ebe6c55754ae3759a28c6df65eadaa11604ad63244f0fdc0aed22802b571b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397462"
---
# <a name="msbuild-task"></a>MSBuild (attività)

Compila MSBuild progetti da un altro MSBuild progetto.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `MSBuild` .

| Parametro | Descrizione |
|-----------------------------------| - |
| `BuildInParallel` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i progetti specificati nel parametro `Projects` vengono compilati in parallelo, se possibile. Il valore predefinito è `false`. |
| `Projects` | Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di progetto da compilare. |
| `Properties` | Parametro `String` facoltativo.<br /><br /> Elenco delimitato da punti e virgola di coppie nome/valore delle proprietà da applicare come proprietà globali al progetto figlio. Quando si specifica questo parametro, è equivalente dal punto di vista funzionale all'impostazione di proprietà con l'opzione **-property** quando si esegue la compilazione [*conMSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Esempio:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Quando si passano proprietà al progetto tramite il parametro , MSBuild possibile creare una nuova istanza del progetto anche se il file di progetto `Properties` è già stato caricato. MSBuild crea una singola istanza del progetto per un percorso di progetto specificato e un set univoco di proprietà globali. Questo comportamento, ad esempio, consente di creare più attività MSBuild che chiamano *myproject.proj* con Configuration=Release, ottenendo una singola istanza di *myproject.proj* (se nell'attività non sono specificate proprietà univoche). Se si specifica una proprietà che non è ancora stata vista da MSBuild, MSBuild crea una nuova istanza del progetto, che può essere compilata in parallelo ad altre istanze del progetto. Una configurazione per il rilascio, ad esempio, può essere compilata contemporaneamente a una configurazione per il debug.|
| `RebaseOutputs` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i percorsi relativi degli elementi di output di destinazione dai progetti compilati vengono modificati in modo da essere percorsi relativi al progetto chiamante. Il valore predefinito è `false`. |
| `RemoveProperties` | Parametro `String` facoltativo.<br /><br /> Specifica il set di proprietà globali da rimuovere. |
| `RunEachTargetSeparately` | Parametro `Boolean` facoltativo.<br /><br /> Se , l'attività MSBuild richiama ogni destinazione nell'elenco passato MSBuild una alla volta, anziché `true` contemporaneamente. Impostare questo parametro su `true` garantisce che le destinazioni successive vengano richiamate anche se le destinazioni richiamate prima hanno avuto esito negativo. In caso contrario, un errore di compilazione arresterà la chiamata di tutte le destinazioni successive. Il valore predefinito è `false`. |
| `SkipNonexistentProjects` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i file di progetto che non esistono sul disco verranno ignorati. In caso contrario, tali progetti genereranno un errore. |
|`SkipNonexistentTargets`|Parametro `Boolean` facoltativo.<br /><br /> Se `true` , i file di progetto che esistono ma non contengono il nome verranno `Targets` ignorati. In caso contrario, tali progetti genereranno un errore. Introdotto in MSBuild 15.5.|
| `StopOnFirstFailure` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, quando la compilazione di uno dei progetti non riesce, non verranno compilati altri progetti. Questo parametro non è attualmente supportato con la compilazione in parallelo (con più processori). |
| `TargetAndPropertyListSeparators` | Parametro `String[]` facoltativo.<br /><br /> Specifica un elenco di destinazioni e proprietà come metadati dell'elemento `Project`. Il carattere di escape verrà rimosso dai separatori prima dell'elaborazione. Ad esempio, %3B (";" preceduto da un carattere di escape) verrà considerato come ";" non preceduto da un carattere di escape. |
| `TargetOutputs` | Parametro di output di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Restituisce gli output delle destinazioni compilate da tutti i file di progetto. Vengono restituiti solo gli output dalle destinazioni specificate, non tutti gli output esistenti nelle destinazioni da cui le destinazioni dipendono.<br /><br /> Il parametro `TargetOutputs` contiene anche i metadati seguenti:<br /><br /> -   `MSBuildSourceProjectFile`: file MSBuild di progetto che contiene la destinazione che imposta gli output.<br />-   `MSBuildSourceTargetName`: destinazione che imposta gli output. **Nota:** per identificare gli output da ogni file di progetto o destinazione separatamente, eseguire l'attività `MSBuild` separatamente per ogni file di progetto o destinazione. Se si esegue l'attività `MSBuild` solo una volta per compilare tutti i file di progetto, gli output di tutte le destinazioni vengono raccolte in una sola matrice. |
| `Targets` | Parametro `String` facoltativo.<br /><br /> Specifica la destinazione o le destinazioni da compilare nei file di progetto. Usare un punto e virgola per separare le voci di un elenco di nomi di destinazione. Se nessuna destinazione viene specificata nell'attività `MSBuild`, vengono compilate le destinazioni predefinite specificate nei file di progetto. **Nota:** le destinazioni devono essere presenti in tutti i file di progetto. In caso contrario, si verifica un errore di compilazione. |
| `ToolsVersion` | Parametro `String` facoltativo.<br /><br /> Specifica la `ToolsVersion` da usare quando si compilano i progetti passati a questa attività.<br /><br /> Consente a MSBuild di compilare un progetto destinato a una versione diversa del .NET Framework rispetto a quella specificata nel progetto. I valori validi sono `2.0`, `3.0` e `3.5`. Il valore predefinito è `3.5`. |

## <a name="remarks"></a>Commenti

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

 A differenza [dell'uso dell'attività Exec](../msbuild/exec-task.md) *MSBuild.exe*, questa attività usa lo stesso processo MSBuild per compilare i progetti figlio. L'elenco di destinazioni già compilate che possono essere ignorate viene condiviso tra le compilazioni padre e figlio. Questa attività è anche più veloce perché non viene MSBuild nuovo processo.

 Questa attività può elaborare non solo i file di progetto, ma anche i file di soluzione.

 Qualsiasi configurazione richiesta da MSBuild per consentire la compilazione dei progetti contemporaneamente, anche se la configurazione implica un'infrastruttura remota (ad esempio porte, protocolli, timeout, tentativi e così via), deve essere resa configurabile tramite un file di configurazione. Se possibile, gli elementi di configurazione devono essere specificati come parametri dell'attività nell'attività `MSBuild`.

 A partire MSBuild 3.5, i progetti di soluzione ora espandono TargetOutput da tutti i sottoprogetti compilati.

## <a name="pass-properties-to-projects"></a>Passare proprietà a progetti

 Nelle versioni di MSBuild precedenti MSBuild 3.5, il passaggio di set diversi di proprietà a progetti diversi elencati nell'elemento MSBuild era difficile. Se è stato usato l'attributo Properties dell'attività [MSBuild](../msbuild/msbuild-task.md), la relativa impostazione è stata applicata a tutti i progetti compilati, a meno che l'attività MSBuild non sia stata in batch e non siano state fornite [in](../msbuild/msbuild-task.md) modo condizionale proprietà diverse per ogni progetto nell'elenco di elementi.

 MSBuild 3.5, tuttavia, fornisce due nuovi elementi di metadati riservati, Properties e AdditionalProperties, che offrono un modo flessibile per passare proprietà diverse per i diversi progetti compilati usando l'attività [MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Questi nuovi elementi di metadati sono applicabili solo agli elementi passati nell'attributo Projects [dell'MSBuild attività](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Vantaggi della compilazione a più processori

 Uno dei vantaggi principali derivanti dall'uso di questi nuovi metadati consiste nel compilare i progetti in parallelo in un sistema a più processori. I metadati consentono di consolidare tutti i progetti in [un'unica chiamata MSBuild](../msbuild/msbuild-task.md) attività senza dover eseguire attività di invio in batch o MSBuild attività. Quando si chiama una sola attività [MSBuild,](../msbuild/msbuild-task.md)tutti i progetti elencati nell'attributo Projects verranno compilati in parallelo. (Solo, tuttavia, se `BuildInParallel=true` l'attributo è presente [nell'attività MSBuild.](../msbuild/msbuild-task.md) Per altre informazioni, vedere [Compilare più progetti in parallelo.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="properties-metadata"></a>Metadati Properties

 Quando specificati, i metadati Properties eseguono l'override del parametro Properties dell'attività, mentre i metadati [AdditionalProperties](#additionalproperties-metadata) vengono accodati alle definizioni del parametro.

 Uno scenario comune è quando si compilano più file di soluzione usando [l'attività MSBuild](../msbuild/msbuild-task.md), usando solo configurazioni di compilazione diverse. Potrebbe essere necessario compilare la soluzione a1 usando la configurazione per il debug e la soluzione a2 usando la configurazione per la versione. In MSBuild 2.0 questo file di progetto sarà simile al seguente:

> [!NOTE]
> Nell'esempio seguente "…" rappresenta file di soluzione aggiuntivi.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Usando i metadati Properties, tuttavia, è possibile semplificare questa operazione per usare una singola attività MSBuild [,](../msbuild/msbuild-task.md)come illustrato di seguito:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <Properties>Configuration=Debug</Properties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"/>
    </Target>
</Project>
```

 \- - oppure -

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Debug"/>
    </Target>
</Project>
```

## <a name="additionalproperties-metadata"></a>Metadati AdditionalProperties

 Si consideri lo scenario seguente in cui si compilano due file di soluzione usando l'attività [MSBuild ,](../msbuild/msbuild-task.md)entrambi usando la configurazione Release, ma uno che usa l'architettura x86 e l'altro usando l'architettura ia64. In MSBuild 2.0 è necessario creare più istanze dell'attività [MSBuild:](../msbuild/msbuild-task.md)una per compilare il progetto usando la configurazione Release con l'architettura x86, l'altra usando la configurazione Release con l'architettura ia64. Il file di progetto sarà come il seguente:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 Usando i metadati AdditionalProperties, è possibile semplificare questa operazione per usare una singola MSBuild [attività](../msbuild/msbuild-task.md) usando quanto segue:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <AdditionalProperties>Architecture=x86
              </AdditionalProperties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <AdditionalProperties>Architecture=ia64
              </AdditionalProperties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Release"/>
    </Target>
</Project>
```

## <a name="example"></a>Esempio

 L'esempio seguente usa l'attività `MSBuild` per compilare i progetti specificati dalla raccolta di elementi `ProjectReferences`. Gli output di destinazione risultanti vengono archiviati nella raccolta di elementi `AssembliesBuiltByChildProjects`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ProjectReferences Include="*.*proj" />
    </ItemGroup>

    <Target Name="BuildOtherProjects">
        <MSBuild
            Projects="@(ProjectReferences)"
            Targets="Build">
            <Output
                TaskParameter="TargetOutputs"
                ItemName="AssembliesBuiltByChildProjects" />
        </MSBuild>
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
