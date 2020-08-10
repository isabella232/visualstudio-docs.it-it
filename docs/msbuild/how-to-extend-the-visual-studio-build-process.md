---
title: Estendere il processo di compilazione
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac3bebc0a64f814e71e7b5ab30282a70fd7eb85e
ms.sourcegitcommit: d293c0e3e9cc71bd4117b6dfd22990d52964addc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2020
ms.locfileid: "88041038"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Procedura: Estendere il processo di compilazione di Visual Studio

Il processo di compilazione di Visual Studio è definito da una serie di file MSBuild *. targets* importati nel file di progetto. Uno di questi file importati, *Microsoft. Common. targets*, può essere esteso per consentire l'esecuzione di attività personalizzate in diversi punti del processo di compilazione. Questo articolo illustra due metodi che è possibile usare per estendere il processo di compilazione di Visual Studio:

- Override di destinazioni predefinite specifiche definite nelle destinazioni comuni (*Microsoft. Common. targets* o i file che importa).

- Override delle proprietà "DependsOn" definite nelle destinazioni comuni.

## <a name="override-predefined-targets"></a>Eseguire l'override di destinazioni predefinite

Le destinazioni comuni contengono un set di destinazioni vuote predefinite che vengono chiamate prima e dopo alcune delle destinazioni principali nel processo di compilazione. Ad esempio, MSBuild chiama la `BeforeBuild` destinazione prima della `CoreBuild` destinazione principale e della `AfterBuild` destinazione dopo la destinazione `CoreBuild` . Per impostazione predefinita, le destinazioni vuote nelle destinazioni comuni non eseguono alcuna operazione, ma è possibile eseguire l'override del comportamento predefinito definendo le destinazioni desiderate in un file di progetto che importa le destinazioni comuni. Eseguendo l'override delle destinazioni predefinite, è possibile usare le attività di MSBuild per fornire un maggiore controllo sul processo di compilazione.

> [!NOTE]
> I progetti in stile SDK hanno un'importazione implicita di destinazioni *dopo l'ultima riga del file di progetto*. Ciò significa che non è possibile eseguire l'override delle destinazioni predefinite a meno che non si specifichino manualmente le importazioni, come descritto in [procedura: usare gli SDK di progetto MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Per eseguire l'override di una destinazione predefinita

1. Identificare una destinazione predefinita nelle destinazioni comuni di cui si vuole eseguire l'override. Nella tabella seguente è riportato l'elenco completo delle destinazioni di cui è possibile eseguire l'override in totale sicurezza.

2. Definire le destinazioni alla fine del file di progetto, immediatamente prima del tag `</Project>`. Ad esempio:

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

La tabella seguente mostra tutte le destinazioni nelle destinazioni comuni di cui è possibile eseguire l'override in modo sicuro.

|Nome di destinazione|Descrizione|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il completamento della compilazione principale. La maggior parte delle personalizzazioni avviene in una di queste due destinazioni.|
|`BeforeBuild`, `AfterBuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo qualsiasi altra attività nella compilazione. **Nota:** le destinazioni `BeforeBuild` e `AfterBuild` sono già definite nei commenti alla fine della maggior parte dei file di progetto, consentendo di aggiungere facilmente eventi di pre e post-compilazione nel file di progetto.|
|`BeforeRebuild`, `AfterRebuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la ricompilazione. L'ordine di esecuzione della destinazione in *Microsoft. Common. targets* è: `BeforeRebuild` ,, `Clean` `Build` e quindi `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pulitura.|
|`BeforePublish`, `AfterPublish`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pubblicazione.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la risoluzione dei riferimenti all'assembly.|
|`BeforeResGen`, `AfterResGen`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la generazione delle risorse.|

## <a name="example-aftertargets-and-beforetargets"></a>Esempio: AfterTargets e BeforeTargets

Nell'esempio seguente viene illustrato come utilizzare l' `AfterTargets` attributo per aggiungere una destinazione personalizzata che esegue un'operazione con i file di output. In questo caso, copia i file di output in una nuova cartella *CustomOutput*.  Nell'esempio viene inoltre illustrato come eseguire la pulizia dei file creati dall'operazione di compilazione personalizzata con una `CustomClean` destinazione utilizzando un `BeforeTargets` attributo e specificando che l'operazione di pulizia personalizzata viene eseguita prima della `CoreClean` destinazione.

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
> Assicurarsi di usare nomi diversi dalle destinazioni predefinite elencate nella tabella della sezione precedente (ad esempio, è stato denominato qui la destinazione di compilazione personalizzata `CustomAfterBuild` `AfterBuild` ), perché tali destinazioni predefinite vengono sostituite dall'importazione dell'SDK che le definisce anche. Non viene visualizzata l'importazione del file di destinazione che esegue l'override di tali destinazioni, ma viene aggiunto in modo implicito alla fine del file di progetto quando si usa il `Sdk` metodo di attributo per fare riferimento a un SDK.

## <a name="override-dependson-properties"></a>Eseguire l'override delle proprietà DependsOn

L'override di destinazioni predefinite è un modo semplice per estendere il processo di compilazione, ma poiché MSBuild valuta la definizione delle destinazioni in modo sequenziale, non è possibile impedire a un altro progetto che importa il progetto di eseguire l'override delle destinazioni di cui è già stato eseguito l'override. Di conseguenza, ad esempio, l'ultima destinazione `AfterBuild` definita nel file di progetto, al termine dell'importazione di tutti gli altri progetti, sarà quella usata durante la compilazione.

È possibile proteggere gli override imprevisti delle destinazioni eseguendo l'override delle proprietà DependsOn utilizzate negli attributi nelle `DependsOnTargets` destinazioni comuni. Nella destinazione `Build`, ad esempio, il valore dell'attributo `DependsOnTargets` è `"$(BuildDependsOn)"`. Tenere in considerazione:

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

È possibile eseguire l'override di questo valore di proprietà dichiarando un'altra proprietà denominata `BuildDependsOn` alla fine del file di progetto. L'inclusione della proprietà `BuildDependsOn` precedente nella nuova proprietà consente di aggiungere nuove destinazioni all'inizio e alla fine dell'elenco di destinazioni. Ad esempio:

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

L'esempio seguente è simile all' `BeforeTargets` esempio e `AfterTargets` , ma Mostra come ottenere una funzionalità simile. Estende la compilazione usando `BuildDependsOn` per aggiungere un'attività personalizzata `CustomAfterBuild` che copia i file di output dopo la compilazione e aggiunge anche l' `CustomClean` attività corrispondente usando `CleanDependsOn` .  

In questo esempio si tratta di un progetto in stile SDK. Come indicato nella nota sui progetti di tipo SDK precedenti in questo articolo, è necessario usare il metodo di importazione manuale anziché l' `Sdk` attributo usato da Visual Studio per generare file di progetto.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

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
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

L'ordine degli elementi è importante. Gli `BuildDependsOn` `CleanDependsOn` elementi e devono essere visualizzati dopo aver importato il file di destinazioni SDK standard.

## <a name="see-also"></a>Vedere anche

- [integrazione con Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [file con estensione targets](../msbuild/msbuild-dot-targets-files.md)
