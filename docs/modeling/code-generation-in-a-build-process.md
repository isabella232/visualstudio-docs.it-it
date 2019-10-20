---
title: Generazione di codice in un processo di compilazione
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c9cc0d8a40970e2ec36030ab3121d6fc02748e2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654203"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Richiama trasformazione testo nel processo di compilazione

La [trasformazione del testo](../modeling/code-generation-and-t4-text-templates.md) può essere richiamata come parte del processo di [compilazione](/azure/devops/pipelines/index) di una soluzione di Visual Studio. Esistono attività di compilazione che sono specializzate nella trasformazione del testo. Le attività di compilazione di T4 eseguono modelli di testo della fase di progettazione e compilano anche modelli di testo (pre-elaborati) della fase di esecuzione.

Esistono alcune differenze in ciò che le attività di compilazione possono fare, a seconda del motore di compilazione utilizzato. Quando si compila la soluzione in Visual Studio, un modello di testo può accedere all'API di Visual Studio (EnvDTE) se è impostato l'attributo [hostspecific = "true"](../modeling/t4-template-directive.md) . Ma ciò non è vero quando si compila la soluzione dalla riga di comando o quando si avvia una compilazione del server tramite Visual Studio. In questi casi, la compilazione viene eseguita da MSBuild e viene utilizzato un diverso host T4. Ciò significa che non è possibile accedere ad elementi come i nomi dei file di progetto nello stesso modo quando si compila un modello di testo tramite MSBuild. Tuttavia, è possibile [passare informazioni sull'ambiente in modelli di testo e processori di direttiva utilizzando parametri di compilazione](#parameters).

## <a name="buildserver"></a>Configurare i computer

Per abilitare le attività di compilazione nel computer di sviluppo, installare Modeling SDK per Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Se [il server di compilazione](/azure/devops/pipelines/agents/agents) è in esecuzione in un computer in cui non è installato Visual Studio, copiare i file seguenti nel computer di compilazione dal computer di sviluppo:

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft. VisualStudio. TextTemplating. Sdk. host. 15.0. dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft. VisualStudio. TextTemplating. 15.0. dll
  - Microsoft. VisualStudio. TextTemplating. Interfaces. 15.0. dll
  - Microsoft. VisualStudio. TextTemplating. VSHost. 15.0. dll

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft. VisualStudio. TextTemplating. Modeling. 15.0. dll

> [!TIP]
> Se si ottiene un `MissingMethodException` per un metodo Microsoft. CodeAnalysis quando si eseguono destinazioni di compilazione TextTemplating in un server di compilazione, assicurarsi che gli assembly Roslyn si trovino in una directory denominata *Roslyn* che si trova nella stessa directory del file eseguibile di compilazione, ad esempio  *MSBuild. exe*).

## <a name="edit-the-project-file"></a>Modificare il file di progetto

Modificare il file di progetto per configurare alcune delle funzionalità di MSBuild, ad esempio l'importazione delle destinazioni di trasformazione del testo.

In **Esplora soluzioni**scegliere **Scarica** dal menu di scelta rapida del progetto. Ciò consente di modificare il file con estensione csproj o vbproj nell'editor XML. Al termine della modifica, scegliere **ricarica**.

## <a name="import-the-text-transformation-targets"></a>Importare le destinazioni di trasformazione del testo

Nel file con estensione csproj o vbproj, individuare una riga simile alla seguente:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- oppure -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Dopo quella riga, inserire l'importazione del modello di testo:

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>Trasformare i modelli in una compilazione

Esistono alcune proprietà che è possibile inserire all'interno del file di progetto per controllare le attività di trasformazione:

- Eseguire l'attività di trasformazione all'inizio di ogni compilazione:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Sovrascrivere i file di sola lettura, ad esempio perché non sono estratti:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Trasforma ogni modello ogni volta:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Per impostazione predefinita, l'attività MSBuild T4 rigenera un file di output se è più vecchio di:

     - file modello
     - tutti i file inclusi
     - tutti i file precedentemente letti dal modello o da un processore di direttiva utilizzato

     Si tratta di un test di dipendenza più potente rispetto a quello usato dal comando **trasforma tutti i modelli** in Visual Studio, che confronta solo le date del modello e del file di output.

Per eseguire solo le trasformazioni di testo nel progetto, richiamare l'attività TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Per trasformare un modello di testo specifico:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

È possibile usare i caratteri jolly in TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Controllo del codice sorgente

Non esiste un'integrazione incorporata specifica con un sistema di controllo del codice sorgente. Tuttavia, è possibile aggiungere estensioni personalizzate, ad esempio per estrarre e archiviare un file generato. Per impostazione predefinita, l'attività di trasformazione del testo consente di evitare la sovrascrittura di un file contrassegnato come di sola lettura. Quando viene rilevato un file di questo tipo, viene registrato un errore in Visual Studio Elenco errori e l'attività ha esito negativo.

Per specificare che i file di sola lettura devono essere sovrascritti, inserire questa proprietà:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

A meno che non si Personalizza il passaggio di post-elaborazione, viene registrato un avviso nel Elenco errori quando un file viene sovrascritto.

## <a name="customize-the-build-process"></a>Personalizzare il processo di compilazione

Nel processo di compilazione, la trasformazione del testo si verifica prima delle altre attività. È possibile definire le attività che vengono chiamati prima e dopo la trasformazione, impostando le proprietà `$(BeforeTransform)` e `$(AfterTransform)`:

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

In `AfterTransform`, è possibile fare riferimento a elenchi di file:

- GeneratedFiles - un elenco di file scritti dal processo. Per i file che sovrascrivevano i file di sola lettura esistenti, `%(GeneratedFiles.ReadOnlyFileOverwritten)` sarà true. È possibile estrarre questi file dal controllo del codice sorgente.

- NonGeneratedFiles - un elenco di file di sola lettura che non sono stati sovrascritti.

Ad esempio, si definisce un'attività per estrarre GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath e OutputFileName

Queste proprietà sono utilizzate solo da MSBuild. Non influiscono sulla generazione di codice in Visual Studio. Effettuano il reindirizzamento del file di output generato su una cartella o un file diverso. La cartella di destinazione deve esistere.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Una cartella utile per il reindirizzamento a è `$(IntermediateOutputPath)`.

Se si specifica un nome di file di output, avrà la precedenza sull'estensione specificata nella direttiva output nei modelli.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Non è consigliabile specificare un OutputFileName o OutputFilePath se si trasformano i modelli all'interno di Visual Studio usando **Transform All** o eseguendo il generatore di file singolo. Si otterrà un percorso di file diverso a seconda della modalità di attivazione della trasformazione. Questa operazione può generare confusione.

## <a name="add-reference-and-include-paths"></a>Aggiungere riferimenti e percorsi di inclusione

L'host dispone di un set predefinito di percorsi in cui cercare gli assembly a cui si fa riferimento nei modelli. Per aggiungere a questo set:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Per impostare le cartelle in cui verranno cercati i file di inclusione, fornire un elenco separato da punti e virgola. In genere si aggiunge all'elenco di cartelle esistenti.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a>Passare i dati del contesto di compilazione nei modelli

È possibile impostare i valori dei parametri nel file di progetto. Ad esempio, è possibile passare le proprietà di [compilazione](../msbuild/msbuild-properties.md) e le [variabili di ambiente](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

In un modello di testo, impostare `hostspecific` nella direttiva del modello. Usare la direttiva [Parameter](../modeling/t4-parameter-directive.md) per ottenere i valori:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

In un processore di direttiva è possibile chiamare [ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` ottiene i dati da `T4ParameterValues` solo quando si utilizza MSBuild. Quando si trasforma il modello con Visual Studio, i parametri hanno valori predefiniti.

## <a name="msbuild"></a>Usare le proprietà del progetto in un assembly e includere le direttive

Le macro di Visual Studio, ad esempio **$ (SolutionDir),** non funzionano in MSBuild. È possibile utilizzare le proprietà del progetto.

Modificare il file con *estensione csproj* o *VBPROJ* per definire una proprietà del progetto. Questo esempio definisce una proprietà denominata **myLibFolder**:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

È possibile utilizzare la proprietà del progetto in un assembly e includere le direttive:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

Queste direttive ottengono valori da T4parameterValues in MSBuild e negli host di Visual Studio.

## <a name="q--a"></a>Domande e risposte

**Perché si desidera trasformare i modelli nel server di compilazione? Ho già trasformato i modelli in Visual Studio prima di archiviare il codice.**

Se si aggiorna un file incluso o un altro file letto dal modello, Visual Studio non trasforma automaticamente il file. La trasformazione dei modelli come parte della compilazione garantisce che tutti gli elementi siano aggiornati.

**Quali altre opzioni sono disponibili per trasformare i modelli di testo?**

- L' [utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) può essere usata negli script di comando. Nella maggior parte dei casi, è più facile utilizzare MSBuild.

- [Richiama la trasformazione del testo in un'estensione di Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- I [modelli di testo della fase di progettazione](../modeling/design-time-code-generation-by-using-t4-text-templates.md) vengono trasformati da Visual Studio.

- I [modelli di testo](../modeling/run-time-text-generation-with-t4-text-templates.md) in fase di esecuzione vengono trasformati in fase di esecuzione nell'applicazione.

## <a name="see-also"></a>Vedere anche

::: moniker range="vs-2017"

- Nel modello MSbuild di T4 sono disponibili indicazioni valide in `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- Nel modello MSbuild di T4 sono disponibili indicazioni valide in `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Scrivere un modello di testo T4](../modeling/writing-a-t4-text-template.md)
