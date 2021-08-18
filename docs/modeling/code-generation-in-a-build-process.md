---
title: Generazione di codice in un processo di compilazione
description: Informazioni su come richiamare la trasformazione del testo come parte del processo di compilazione di una Visual Studio soluzione.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1cf6376ca9ef5442e4f71588a6de7d3a4a33886ba8520f18914f03d7522fa463
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411321"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Richiamare la trasformazione del testo nel processo di compilazione

[La trasformazione](../modeling/code-generation-and-t4-text-templates.md) del testo può essere richiamata come parte del processo [di compilazione](/azure/devops/pipelines/index) di una Visual Studio soluzione. Esistono attività di compilazione che sono specializzate nella trasformazione del testo. Le attività di compilazione di T4 eseguono modelli di testo della fase di progettazione e compilano anche modelli di testo (pre-elaborati) della fase di esecuzione.

Esistono alcune differenze in ciò che le attività di compilazione possono fare, a seconda del motore di compilazione utilizzato. Quando si compila la soluzione in Visual Studio, un modello di testo può accedere all'API Visual Studio (EnvDTE) se è impostato l'attributo [hostspecific="true".](../modeling/t4-template-directive.md) Ma questo non è vero quando si compila la soluzione dalla riga di comando o quando si avvia una compilazione del server tramite Visual Studio. In questi casi, la compilazione viene eseguita da MSBuild e viene utilizzato un diverso host T4. Ciò significa che non è possibile accedere ad elementi come i nomi di file di progetto nello stesso modo quando si compila un modello di testo usando MSBuild. Tuttavia, è possibile [passare le informazioni sull'ambiente nei modelli di testo e nei processori di direttiva usando i parametri di compilazione](#parameters).

## <a name="configure-your-machines"></a><a name="buildserver"></a> Configurare i computer

Per abilitare le attività di compilazione nel computer di sviluppo, installare Modeling SDK per Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Se [il server di](/azure/devops/pipelines/agents/agents) compilazione viene eseguito in un computer in cui non è installato Visual Studio, copiare i file seguenti nel computer di compilazione dal computer di sviluppo:

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.15.0.dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.Interfaces.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.VSHost.15.0.dll

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft.VisualStudio.TextTemplating.Modeling.15.0.dll

> [!TIP]
> Se si ottiene un oggetto per un metodo Microsoft.CodeAnalysis quando si esegue TextTemplating build targets in un server di compilazione, assicurarsi che gli assembly Roslyn siano in una directory denominata `MissingMethodException` *Roslyn* nella stessa directory del file eseguibile di compilazione , ad esempio *msbuild.exe*.

## <a name="edit-the-project-file"></a>Modificare il file di progetto

Modificare il file di progetto per configurare alcune delle funzionalità di MSBuild, ad esempio l'importazione delle destinazioni di trasformazione del testo.

In **Esplora soluzioni** scegliere **Scarica dal** menu di scelta rapida del progetto. Ciò consente di modificare il file con estensione csproj o vbproj nell'editor XML. Al termine della modifica, scegliere **Ricarica**.

## <a name="import-the-text-transformation-targets"></a>Importare le destinazioni di trasformazione del testo

Nel file con estensione csproj o vbproj, individuare una riga simile alla seguente:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- - oppure -

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

     Per impostazione predefinita, l'attività T4 MSBuild rigenera un file di output se è precedente a:

     - file modello
     - tutti i file inclusi
     - tutti i file letti in precedenza dal modello o da un processore di direttiva che usa

     Si tratta di un test delle dipendenze più potente di quello usato dal comando Trasforma tutti i modelli in Visual Studio, che confronta solo le date del modello e del file di output. 

Per eseguire solo le trasformazioni di testo nel progetto, richiamare l'attività TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Per trasformare un modello di testo specifico:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

È possibile usare i caratteri jolly in TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Controllo del codice sorgente

Non esiste un'integrazione incorporata specifica con un sistema di controllo del codice sorgente. È tuttavia possibile aggiungere estensioni personalizzate, ad esempio per estrarre e archiviare un file generato. Per impostazione predefinita, l'attività di trasformazione del testo evita la sovrascrittura di un file contrassegnato come di sola lettura. Quando viene rilevato un file di questo tipo, viene registrato un errore nell'elenco Visual Studio errori e l'attività ha esito negativo.

Per specificare che i file di sola lettura devono essere sovrascritti, inserire questa proprietà:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

A meno che non si personalizza il passaggio di post-elaborazione, quando un file viene sovrascritto verrà registrato un avviso nell'Elenco errori.

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

- GeneratedFiles - un elenco di file scritti dal processo. Per i file che hanno sovrascritto i file di sola lettura esistenti, `%(GeneratedFiles.ReadOnlyFileOverwritten)` sarà true. È possibile estrarre questi file dal controllo del codice sorgente.

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

Una cartella utile a cui reindirizzare è `$(IntermediateOutputPath)` .

Se si specifica un nome file di output, ha la precedenza sull'estensione specificata nella direttiva di output nei modelli.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Non è consigliabile specificare OutputFileName o OutputFilePath se si trasformano anche modelli all'interno di Visual Studio usando **Transform All** o eseguendo il generatore di file singolo. Si finirà con percorsi di file diversi a seconda di come è stata attivata la trasformazione. Questa operazione può risultare poco chiara.

## <a name="add-reference-and-include-paths"></a>Aggiungere percorsi di riferimento e di inclusione

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

## <a name="pass-build-context-data-into-the-templates"></a><a name="parameters"></a> Passare i dati del contesto di compilazione nei modelli

È possibile impostare i valori dei parametri nel file di progetto. Ad esempio, è possibile passare le [proprietà di compilazione](../msbuild/msbuild-properties.md) e le variabili di [ambiente](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

In un modello di testo, impostare `hostspecific` nella direttiva del modello. Usare la [direttiva](../modeling/t4-parameter-directive.md) parameter per ottenere i valori:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

In un processore di direttiva è possibile chiamare [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue`ottiene i dati `T4ParameterValues` da solo quando si usa MSBuild. Quando si trasforma il modello usando Visual Studio, i parametri hanno valori predefiniti.

## <a name="use-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Usare le proprietà del progetto nell'assembly e includere le direttive

Visual Studio macro come **$(SolutionDir)** non funzionano in MSBuild. È possibile utilizzare le proprietà del progetto.

Modificare il *file con estensione csproj* o *vbproj* per definire una proprietà del progetto. In questo esempio viene definita una proprietà **denominata myLibFolder**:

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

**Perché è necessario trasformare i modelli nel server di compilazione? I modelli sono già stati trasformati in Visual Studio prima di archiviare il codice.**

Se si aggiorna un file incluso o un altro file letto dal modello, Visual Studio il file non viene trasformato automaticamente. La trasformazione dei modelli come parte della compilazione garantisce che tutto sia aggiornato.

**Quali altre opzioni ci sono per trasformare i modelli di testo?**

- [L'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) può essere usata negli script di comando. Nella maggior parte dei casi, è più semplice usare MSBuild.

- [Richiamare la trasformazione testo in un'estensione Visual Studio testo](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- [I modelli di testo in fase di](../modeling/design-time-code-generation-by-using-t4-text-templates.md) progettazione vengono trasformati Visual Studio.

- [I modelli di testo in fase di](../modeling/run-time-text-generation-with-t4-text-templates.md) esecuzione vengono trasformati in fase di esecuzione nell'applicazione.

## <a name="see-also"></a>Vedi anche

::: moniker range="vs-2017"

- Nel modello T4 MSbuild sono disponibili indicazioni utili all'indirizzo `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- Nel modello T4 MSbuild sono disponibili indicazioni utili all'indirizzo `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Scrivere un modello di testo T4](../modeling/writing-a-t4-text-template.md)
