---
title: Attività MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab54c5c523c833be60ef4b5d5088b6217a3111a5
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072580"
---
# <a name="msbuild-task"></a>MSBuild (attività)

Compila progetti MSBuild da un altro progetto MSBuild.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `MSBuild` .

| Parametro | Descrizione |
|-----------------------------------| - |
| `BuildInParallel` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i progetti specificati nel parametro `Projects` vengono compilati in parallelo, se possibile. Il valore predefinito è `false`. |
| `Projects` | Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di progetto da compilare. |
| `Properties` | Parametro `String` facoltativo.<br /><br /> Elenco delimitato da punti e virgola di coppie nome/valore delle proprietà da applicare come proprietà globali al progetto figlio. Quando si specifica questo parametro, è funzionalmente equivalente all'impostazione di proprietà con l'opzione **-property** quando si compila con [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Ad esempio:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Quando si passano le `Properties` proprietà al progetto tramite il parametro , MSBuild potrebbe creare una nuova istanza del progetto anche se il file di progetto è già stato caricato. MSBuild crea una singola istanza di progetto per un determinato percorso di progetto e un set univoco di proprietà globali. Questo comportamento, ad esempio, consente di creare più attività MSBuild che chiamano *myproject.proj* con Configuration=Release, ottenendo una singola istanza di *myproject.proj* (se nell'attività non sono specificate proprietà univoche). Se si specifica una proprietà che non è stata ancora visualizzata da MSBuild, MSBuild crea una nuova istanza del progetto, che può essere compilata in parallelo ad altre istanze del progetto. Una configurazione per il rilascio, ad esempio, può essere compilata contemporaneamente a una configurazione per il debug.|
| `RebaseOutputs` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i percorsi relativi degli elementi di output di destinazione dai progetti compilati vengono modificati in modo da essere percorsi relativi al progetto chiamante. Il valore predefinito è `false`. |
| `RemoveProperties` | Parametro `String` facoltativo.<br /><br /> Specifica il set di proprietà globali da rimuovere. |
| `RunEachTargetSeparately` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività MSBuild richiama ogni destinazione nell'elenco passato a MSBuild uno alla volta, anziché contemporaneamente. Impostare questo parametro su `true` garantisce che le destinazioni successive vengano richiamate anche se le destinazioni richiamate prima hanno avuto esito negativo. In caso contrario, un errore di compilazione arresterà la chiamata di tutte le destinazioni successive. Il valore predefinito è `false`. |
| `SkipNonexistentProjects` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i file di progetto che non esistono sul disco verranno ignorati. In caso contrario, tali progetti genereranno un errore. |
|`SkipNonexistentTargets`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i file di progetto `Targets` che esistono ma non contengono il nome verranno ignorati. In caso contrario, tali progetti genereranno un errore. Introdotto in MSBuild 15.5.|
| `StopOnFirstFailure` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, quando la compilazione di uno dei progetti non riesce, non verranno compilati altri progetti. Questo parametro non è attualmente supportato con la compilazione in parallelo (con più processori). |
| `TargetAndPropertyListSeparators` | Parametro `String[]` facoltativo.<br /><br /> Specifica un elenco di destinazioni e proprietà come metadati dell'elemento `Project`. Il carattere di escape verrà rimosso dai separatori prima dell'elaborazione. Ad esempio, %3B (";" preceduto da un carattere di escape) verrà considerato come ";" non preceduto da un carattere di escape. |
| `TargetOutputs` | Parametro di output di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Restituisce gli output delle destinazioni compilate da tutti i file di progetto. Vengono restituiti solo gli output dalle destinazioni specificate, non tutti gli output esistenti nelle destinazioni da cui le destinazioni dipendono.<br /><br /> Il parametro `TargetOutputs` contiene anche i metadati seguenti:<br /><br /> -   `MSBuildSourceProjectFile`: il file di progetto MSBuild che contiene la destinazione che imposta gli output.<br />-   `MSBuildSourceTargetName`: destinazione che imposta gli output. **Nota:** per identificare gli output da ogni file di progetto o destinazione separatamente, eseguire l'attività `MSBuild` separatamente per ogni file di progetto o destinazione. Se si esegue l'attività `MSBuild` solo una volta per compilare tutti i file di progetto, gli output di tutte le destinazioni vengono raccolte in una sola matrice. |
| `Targets` | Parametro `String` facoltativo.<br /><br /> Specifica la destinazione o le destinazioni da compilare nei file di progetto. Usare un punto e virgola per separare le voci di un elenco di nomi di destinazione. Se nessuna destinazione viene specificata nell'attività `MSBuild`, vengono compilate le destinazioni predefinite specificate nei file di progetto. **Nota:** le destinazioni devono essere presenti in tutti i file di progetto. In caso contrario, si verifica un errore di compilazione. |
| `ToolsVersion` | Parametro `String` facoltativo.<br /><br /> Specifica la `ToolsVersion` da usare quando si compilano i progetti passati a questa attività.<br /><br /> Consente a un'attività MSBuild di compilare un progetto destinato a una versione di .NET Framework diversa da quella specificata nel progetto. I valori validi sono `2.0`, `3.0` e `3.5`. Il valore predefinito è `3.5`. |

## <a name="remarks"></a>Osservazioni

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [TaskExtension base class](../msbuild/taskextension-base-class.md).

 A differenza [dell'utilizzo dell'attività Exec](../msbuild/exec-task.md) per avviare *MSBuild.exe,* questa attività utilizza lo stesso processo MSBuild per compilare i progetti figlio. L'elenco di destinazioni già compilate che possono essere ignorate viene condiviso tra le compilazioni padre e figlio. Questa attività è anche più veloce perché non viene creato alcun nuovo processo MSBuild.This task is also faster because no new MSBuild process is created.

 Questa attività può elaborare non solo i file di progetto, ma anche i file di soluzione.

 Qualsiasi configurazione richiesta da MSBuild per consentire la compilazione contemporanea dei progetti, anche se la configurazione coinvolge l'infrastruttura remota (ad esempio, porte, protocolli, timeout, tentativi e così via), deve essere resa configurabile tramite un file di configurazione. Se possibile, gli elementi di configurazione devono essere specificati come parametri dell'attività nell'attività `MSBuild`.

 A partire da MSBuild 3.5, i progetti di soluzione ora elevano TargetOutputs da tutti i sottoprogetti compilati.

## <a name="pass-properties-to-projects"></a>Passare proprietà a progetti

 Nelle versioni di MSBuild precedenti a MSBuild 3.5, il passaggio di diversi set di proprietà a progetti diversi elencati nell'elemento MSBuild era difficile. Se è stato utilizzato l'attributo Properties [dell'attività MSBuild](../msbuild/msbuild-task.md), la relativa impostazione è stata applicata a tutti i progetti compilati, a meno che l'attività [MSBuild non](../msbuild/msbuild-task.md) sia stata creata in batch e non siano state fornite in modo condizionale proprietà diverse per ogni progetto nell'elenco di elementi.

 MSBuild 3.5, tuttavia, fornisce due nuovi elementi di metadati riservati, Properties e AdditionalProperties, che forniscono un modo flessibile per passare proprietà diverse per progetti diversi compilati utilizzando [l'attività MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Questi nuovi elementi di metadati sono applicabili solo agli elementi passati nell'attributo Projects [dell'attività MSBuild.](../msbuild/msbuild-task.md)

## <a name="multi-processor-build-benefits"></a>Vantaggi della compilazione a più processori

 Uno dei vantaggi principali derivanti dall'uso di questi nuovi metadati consiste nel compilare i progetti in parallelo in un sistema a più processori. I metadati consentono di consolidare tutti i progetti in una singola chiamata di [attività MSBuild](../msbuild/msbuild-task.md) senza dover eseguire attività MSBuild in batch o condizionali. E quando si chiama solo una singola [attività MSBuild](../msbuild/msbuild-task.md), tutti i progetti elencati nell'attributo Projects verranno compilati in parallelo. (Solo, tuttavia, `BuildInParallel=true` se l'attributo è presente nell'attività [MSBuild](../msbuild/msbuild-task.md). Per ulteriori informazioni, consultate [Compilare più progetti in parallelo.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="properties-metadata"></a>Metadati Properties

 Quando specificati, i metadati Properties eseguono l'override del parametro Properties dell'attività, mentre i metadati [AdditionalProperties](#additionalproperties-metadata) vengono accodati alle definizioni del parametro.

 Uno scenario comune si verifica quando si compilano più file di soluzione utilizzando [l'attività MSBuild,](../msbuild/msbuild-task.md)utilizzando solo configurazioni di compilazione diverse. Potrebbe essere necessario compilare la soluzione a1 usando la configurazione per il debug e la soluzione a2 usando la configurazione per la versione. In MSBuild 2.0, questo file di progetto sarebbe simile al seguente:In MSBuild 2.0, this project file would look like the following:

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

 Utilizzando i metadati Properties, tuttavia, è possibile semplificare questa operazione per utilizzare una singola [attività MSBuild,](../msbuild/msbuild-task.md)come illustrato di seguito:

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

 Si consideri lo scenario seguente in cui si creano due file della soluzione utilizzando [l'attività MSBuild,](../msbuild/msbuild-task.md)entrambi utilizzando la configurazione di rilascio, ma uno utilizzando l'architettura x86 e l'altro utilizzando l'architettura ia64. In MSBuild 2.0, è necessario creare più istanze [dell'attività MSBuild:](../msbuild/msbuild-task.md)una per compilare il progetto utilizzando la configurazione di rilascio con l'architettura x86, l'altra usando la configurazione Release con l'architettura ia64. Il file di progetto sarà come il seguente:

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

 Utilizzando i metadati AdditionalProperties, è possibile semplificare questa operazione per utilizzare una singola [attività MSBuild](../msbuild/msbuild-task.md) usando quanto segue:

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

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
