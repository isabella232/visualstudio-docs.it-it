---
title: Generazione del codice in un processo di compilazione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: abb37b7bdfbc01affea63aa90d35b3702dcb4719
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907924"
---
# <a name="code-generation-in-a-build-process"></a>Generazione di codice in un processo di compilazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Trasformazione del testo può essere richiamate come parte del processo di compilazione di una soluzione di Visual Studio. Esistono attività di compilazione che sono specializzate nella trasformazione del testo. Le attività di compilazione di T4 eseguono modelli di testo della fase di progettazione e compilano anche modelli di testo (pre-elaborati) della fase di esecuzione.

Esistono alcune differenze in ciò che le attività di compilazione possono fare, a seconda del motore di compilazione utilizzato. Quando si compila la soluzione in Visual Studio, un modello di testo può accedere alle API di Visual Studio (EnvDTE) se il [hostspecific = "true"](../modeling/t4-template-directive.md) attributo è impostato. Ma ciò non accade quando si compila la soluzione da riga di comando o quando si avvia una compilazione per server tramite Visual Studio. In questi casi, la compilazione viene eseguita da MSBuild e viene utilizzato un diverso host T4.

Ciò significa che non è possibile accedere a elementi quali i nomi dei file di progetto allo stesso modo di quando si compila un modello di testo in MSBuild. Tuttavia, è possibile [passare le informazioni sull'ambiente in modelli di testo e processori di direttive utilizzando parametri di compilazione](#parameters).

##  <a name="buildserver"></a> Configurare i computer

Per abilitare le attività di compilazione nel computer di sviluppo, installare [Modeling SDK per Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754).

Se [il server di compilazione](http://msdn.microsoft.com/library/788443c3-0547-452e-959c-4805573813a9) viene eseguita in un computer in cui non è installato Visual Studio, copiare i file seguenti nel computer di compilazione dal computer di sviluppo. Sostituire ‘*’ con il numero dell'ultima versione.

-   $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    -   Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    -   Microsoft.TextTemplating.Build.Tasks.dll

    -   Microsoft.TextTemplating.targets

-   $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    -   Microsoft.VisualStudio.TextTemplating.*.0.dll

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (più file)

    -   Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

-   $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    -   Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Per modificare il file di progetto

Sarà necessario modificare il file di progetto per configurare alcune funzionalità di MSBuild.

In Esplora soluzioni, scegliere **Unload** dal menu di scelta rapida del progetto. Ciò consente di modificare il file con estensione csproj o vbproj nell'editor XML.

Al termine della modifica, scegliere **Ricarica**.

## <a name="import-the-text-transformation-targets"></a>Importare le destinazioni della trasformazione del testo

Nel file con estensione csproj o vbproj, individuare una riga simile alla seguente:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- oppure -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Dopo quella riga, inserire l'importazione del modello di testo:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version – defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transforming-templates-in-a-build"></a>Trasformare i modelli in una compilazione

Esistono alcune proprietà che è possibile inserire all'interno del file di progetto per controllare le attività di trasformazione:

-   Eseguire l'attività di trasformazione all'inizio di ogni compilazione:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

-   Sovrascrivere i file di sola lettura, ad esempio perché non sono stati estratti:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

-   Trasforma ogni modello ogni volta:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Per impostazione predefinita, l'attività MSBuild di T4 rigenera un file di output se è meno recente del file del modello, oppure ogni file che è incluso od ogni file che era stato letto dal modello o da un processore di direttiva utilizzato. Si noti che questo è un test delle dipendenze molto più efficace rispetto a quello utilizzato dal comando di Visual Studio Trasforma tutti i modelli, che confronta solo le date del modello e del file di output.

Per eseguire solo le trasformazioni di testo nel progetto, richiamare l'attività TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Per trasformare un modello di testo specifico:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

È possibile utilizzare i caratteri jolly in TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Controllo del codice sorgente

Non esiste un'integrazione incorporata specifica con un sistema di controllo del codice sorgente. Tuttavia è possibile aggiungere estensioni personalizzate, ad esempio per estrarre o archiviare un file generato. Per impostazione predefinita l'attività di trasformazione del testo evita sovrascrivere un file contrassegnato come di sola lettura e quando viene incontrato questo tipo di file, viene registrato un errore nell'elenco errori di Visual Studio e l'attività non viene completata.

Per specificare che i file di sola lettura devono essere sovrascritti, inserire questa proprietà:

`<OverwriteReadOnlyOuputFiles>true</OverwriteReadOnlyOuputFiles>`

A meno che si personalizzi il passaggio di post-elaborazione, quando un file viene sovrascritto, verrà registrato un avviso nell'elenco errori.

## <a name="customizing-the-build-process"></a>Personalizzazione del processo di compilazione

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

- GeneratedFiles - un elenco di file scritti dal processo. Per quelli file che hanno sovrascritto file di sola lettura esistenti,% (GeneratedFiles.ReadOnlyFileOverwritten) sarà true. È possibile estrarre questi file dal controllo del codice sorgente.

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

Una cartella utile verso cui effettuare il reindirizzamento è `$(IntermediateOutputPath).`

Se si specifica un nome per il file di output, esso avrà la precedenza sull'estensione specificata nella direttiva di output dei modelli.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Specificare un OutputFileName o un OutputFilePath non è consigliato se nel frattempo si stanno anche trasformando i modelli in Visual Studio utilizzando Trasforma tutto o si sta eseguendo il generatore di file singolo. Si finirà con l'avere percorsi di file diversi a seconda di come è stata attivata la trasformazione. Ciò può provocare confusione.

## <a name="adding-reference-and-include-paths"></a>Aggiungere riferimenti e percorsi di inclusione

L'host dispone di un set predefinito di percorsi in cui cercare gli assembly a cui si fa riferimento nei modelli. Per aggiungere a questo set:

```
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Per impostare le cartelle in cui verranno cercati i file di inclusione, fornire un elenco separato da punti e virgola. In genere si aggiunge all'elenco di cartelle esistenti.

```
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

##  <a name="parameters"></a> Passare i dati di contesto di compilazione nei modelli

È possibile impostare i valori dei parametri nel file di progetto. Ad esempio, è possibile passare le proprietà di compilazione e [variabili di ambiente](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

In un modello di testo, impostare `hostspecific` nella direttiva del modello. Usare la [parametro](../modeling/t4-parameter-directive.md) direttiva per ottenere valori:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

##  <a name="msbuild"></a> Usando le proprietà del progetto nell'assembly e includere le direttive

Le macro di Visual Studio, ad esempio $(SolutionDir), non funzionano in MSBuild. È possibile utilizzare le proprietà del progetto.

Modificare il file con estensione csproj o vbproj per definire una proprietà del progetto. In questo esempio viene definita una proprietà denominata `myLibFolder`:

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

**Motivo per cui vuole trasformare i modelli nel server di compilazione? Già trasformato modelli in Visual Studio prima di archiviare il codice utente.**

Se si aggiorna un file incluso oppure un altro file letto dal modello, Visual Studio non trasforma il file automaticamente. Trasformare modelli come parte della compilazione garantisce che tutto sia aggiornato.

**Quali altre opzioni sono presenti per la trasformazione dei modelli di testo?**

-   Il [utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) possono essere utilizzati negli script di comando. Nella maggior parte dei casi è più facile utilizzare MSBuild.

-   [Richiamo della trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

-   [Modelli di testo in fase di progettazione](../modeling/design-time-code-generation-by-using-t4-text-templates.md) vengono trasformati da Visual Studio.

-   [Modelli di testo in fase di esecuzione](../modeling/run-time-text-generation-with-t4-text-templates.md) vengono trasformati in fase di esecuzione nell'applicazione.

## <a name="read-more"></a>Altre informazioni

Esiste materiale sussidiario nel modello MSbuild di T4, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets

- [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)
- [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)
- [Oleg Sych: Informazioni T4:MSBuild integrazione](http://www.olegsych.com/2010/04/understanding-t4-msbuild-integration/)