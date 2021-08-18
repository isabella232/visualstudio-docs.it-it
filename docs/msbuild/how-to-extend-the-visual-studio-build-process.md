---
title: Estendere il processo di compilazione
description: Informazioni su vari modi per modificare il processo di compilazione in modo da poter controllare e personalizzare la modalità di compilazione dei progetti.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: db2b813937c4966dd4acd37b6e053cbe533e993c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136937"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Procedura: Estendere il processo di compilazione di Visual Studio

Il Visual Studio di compilazione è definito da una serie di MSBuild con estensione *targets* importati nel file di progetto. Uno di questi file importati, *Microsoft.Common.targets,* può essere esteso per consentire l'esecuzione di attività personalizzate in diversi punti del processo di compilazione. Questo articolo illustra due metodi che è possibile usare per estendere il Visual Studio di compilazione:

- Override di destinazioni predefinite specifiche definite nelle destinazioni comuni (*Microsoft.Common.targets* o nei file importati).

- Override delle proprietà "DependsOn" definite nelle destinazioni comuni.

## <a name="override-predefined-targets"></a>Eseguire l'override di destinazioni predefinite

Le destinazioni comuni contengono un set di destinazioni vuote predefinite chiamate prima e dopo alcune delle destinazioni principali nel processo di compilazione. Ad esempio, MSBuild chiama la destinazione prima della destinazione principale e `BeforeBuild` la destinazione dopo la `CoreBuild` `AfterBuild` `CoreBuild` destinazione. Per impostazione predefinita, le destinazioni vuote nelle destinazioni comuni non eseguono alcuna operazione, ma è possibile eseguirne l'override definendo le destinazioni desiderate in un file di progetto che importa le destinazioni comuni. Eseguendo l'override delle destinazioni predefinite, è possibile usare MSBuild attività per offrire un maggiore controllo sul processo di compilazione.

> [!NOTE]
> I progetti di tipo SDK hanno un'importazione implicita di destinazioni *dopo l'ultima riga del file di progetto*. Ciò significa che non è possibile eseguire l'override delle destinazioni predefinite a meno che non si specificano manualmente le importazioni, come descritto in Procedura: Usare MSBuild [SDK del progetto.](how-to-use-project-sdk.md)

#### <a name="to-override-a-predefined-target"></a>Per eseguire l'override di una destinazione predefinita

1. Identificare una destinazione predefinita nelle destinazioni comuni di cui si vuole eseguire l'override. Nella tabella seguente è riportato l'elenco completo delle destinazioni di cui è possibile eseguire l'override in totale sicurezza.

2. Definire le destinazioni alla fine del file di progetto, immediatamente prima del tag `</Project>`. Esempio:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Compilare il file di progetto.

La tabella seguente illustra tutte le destinazioni nelle destinazioni comuni di cui è possibile eseguire l'override in modo sicuro.

|Nome di destinazione|Descrizione|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il completamento della compilazione principale. La maggior parte delle personalizzazioni avviene in una di queste due destinazioni.|
|`BeforeBuild`, `AfterBuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo qualsiasi altra attività nella compilazione. **Nota:** le destinazioni `BeforeBuild` e `AfterBuild` sono già definite nei commenti alla fine della maggior parte dei file di progetto, consentendo di aggiungere facilmente eventi di pre e post-compilazione nel file di progetto.|
|`BeforeRebuild`, `AfterRebuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la ricompilazione. L'ordine di esecuzione di destinazione in *Microsoft.Common.targets* è: `BeforeRebuild` , , e quindi `Clean` `Build` `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pulitura.|
|`BeforePublish`, `AfterPublish`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pubblicazione.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la risoluzione dei riferimenti all'assembly.|
|`BeforeResGen`, `AfterResGen`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la generazione delle risorse.|

## <a name="example-aftertargets-and-beforetargets"></a>Esempio: AfterTargets e BeforeTargets

Nell'esempio seguente viene illustrato come usare `AfterTargets` l'attributo per aggiungere una destinazione personalizzata che esegue un'azione con i file di output. In questo caso, copia i file di output in una nuova cartella *CustomOutput*.  L'esempio illustra anche come pulire i file creati dall'operazione di compilazione personalizzata con una destinazione usando un attributo e specificando che l'operazione di pulizia personalizzata viene eseguita `CustomClean` `BeforeTargets` prima della `CoreClean` destinazione.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
     <TargetFramework>netcoreapp3.1</TargetFramework>
     <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild" AfterTargets="Build">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

    <Message Text="DestFiles:
        @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles=
          "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Assicurarsi di usare nomi diversi rispetto alle destinazioni predefinite elencate nella tabella nella sezione precedente (ad esempio, la destinazione di compilazione personalizzata è stata denominata qui , non ), perché tali destinazioni predefinite vengono sostituite dall'importazione dell'SDK che le definisce `CustomAfterBuild` `AfterBuild` anche. L'importazione del file di destinazione che esegue l'override di tali destinazioni non viene visualizzata, ma viene aggiunta in modo implicito alla fine del file di progetto quando si usa il metodo attribute per fare riferimento a un `Sdk` SDK.

## <a name="override-dependson-properties"></a>Eseguire l'override delle proprietà DependsOn

L'override delle destinazioni predefinite è un modo semplice per estendere il processo di compilazione, ma, poiché MSBuild valuta in sequenza la definizione delle destinazioni, non è possibile impedire a un altro progetto che importa il progetto di eseguire l'override delle destinazioni di cui è già stato eseguito l'override. Di conseguenza, ad esempio, l'ultima destinazione `AfterBuild` definita nel file di progetto, al termine dell'importazione di tutti gli altri progetti, sarà quella usata durante la compilazione.

È possibile proteggersi da override imprevisti delle destinazioni eseguendo l'override delle proprietà DependsOn usate negli attributi in `DependsOnTargets` tutte le destinazioni comuni. Nella destinazione `Build`, ad esempio, il valore dell'attributo `DependsOnTargets` è `"$(BuildDependsOn)"`. Tenere in considerazione:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Questa parte di codice XML indica che la destinazione `Build` può essere eseguita solo dopo l'esecuzione di tutte le destinazioni specificate nella proprietà `BuildDependsOn`. La proprietà `BuildDependsOn` è definita come segue:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

È possibile eseguire l'override di questo valore di proprietà dichiarando un'altra proprietà denominata `BuildDependsOn` alla fine del file di progetto. L'inclusione della proprietà `BuildDependsOn` precedente nella nuova proprietà consente di aggiungere nuove destinazioni all'inizio e alla fine dell'elenco di destinazioni. Esempio:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

I progetti che importano i file di progetto possono eseguire l'override di queste proprietà senza sovrascrivere le personalizzazioni effettuate in precedenza.

#### <a name="to-override-a-dependson-property"></a>Per eseguire l'override di una proprietà DependsOn

1. Identificare una proprietà DependsOn predefinita nelle destinazioni comuni di cui si vuole eseguire l'override. Nella tabella che segue è riportato un elenco delle proprietà DependsOn comunemente sottoposte a override.

2. Definire un'altra istanza della proprietà o delle proprietà alla fine del file di progetto. Nella nuova proprietà includere la proprietà originale, ad esempio `$(BuildDependsOn)`.

3. Definire le destinazioni personalizzate prima o dopo la definizione della proprietà.

4. Compilare il file di progetto.

### <a name="commonly-overridden-dependson-properties"></a>Proprietà DependsOn comunemente sottoposte a override

|Nome proprietà|Descrizione|
|-------------------|-----------------|
|`BuildDependsOn`|Proprietà di cui eseguire l'override se si vuole inserire destinazioni personalizzate prima o dopo l'intero processo di compilazione.|
|`CleanDependsOn`|Proprietà di cui eseguire l'override se si vuole pulire l'output del processo di compilazione personalizzato.|
|`CompileDependsOn`|Proprietà di cui eseguire l'override se si vuole inserire processi personalizzati prima o dopo la fase di compilazione.|

## <a name="example-builddependson-and-cleandependson"></a>Esempio: BuildDependsOn e CleanDependsOn

L'esempio seguente è simile `BeforeTargets` all'esempio e , ma mostra come ottenere funzionalità `AfterTargets` simili. Estende la compilazione usando per aggiungere un'attività personalizzata che copia i file di output dopo la compilazione e aggiunge anche l'attività `BuildDependsOn` `CustomAfterBuild` corrispondente usando `CustomClean` `CleanDependsOn` .  

In questo esempio si tratta di un progetto di tipo SDK. Come accennato nella nota sui progetti di tipo SDK in precedenza in questo articolo, è necessario usare il metodo di importazione manuale anziché l'attributo che Visual Studio usa quando genera i file `Sdk` di progetto.

```xml
<Project>
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Importance="high" Text="_FilesToCopy: @(_FilesToCopy)"/>

    <Message Text="DestFiles:
      @(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles="@(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Importance="high" Text="Inside Custom Clean"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files="@(_CustomFilesToDelete)"/>
  </Target>
</Project>
```

L'ordine degli elementi è importante. Gli `BuildDependsOn` elementi e devono essere visualizzati dopo `CleanDependsOn` l'importazione del file di destinazione sdk standard.

## <a name="see-also"></a>Vedi anche

- [Visual Studio'integrazione](../msbuild/visual-studio-integration-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [File con estensione targets](../msbuild/msbuild-dot-targets-files.md)
