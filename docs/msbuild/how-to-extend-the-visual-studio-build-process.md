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
ms.openlocfilehash: f6a465a752282f4a0dc00f3fb294ade4169bb19b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093938"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Procedura: Estendere il processo di compilazione di Visual Studio

Il processo di compilazione di Visual Studio è definito da una serie di file *con estensione targets* MSBuild importati nel file di progetto. Uno di questi file importati, *Microsoft.Common.targets*, può essere esteso per consentire l'esecuzione di attività personalizzate in diversi punti del processo di compilazione. In questo articolo vengono illustrati due metodi che è possibile usare per estendere il processo di compilazione di Visual Studio:This article explains two methods you can use to extend the Visual Studio build process:

- Override di destinazioni predefinite specifiche definite nelle destinazioni comuni (*Microsoft.Common.targets* o nei file importati).

- Override delle proprietà "DependsOn" definite nelle destinazioni comuni.

## <a name="override-predefined-targets"></a>Eseguire l'override di destinazioni predefinite

Le destinazioni comuni contiene un set di destinazioni vuote predefinite che viene chiamato prima e dopo alcune delle destinazioni principali nel processo di compilazione. Ad esempio, MSBuild `BeforeBuild` chiama la `CoreBuild` destinazione `AfterBuild` prima della `CoreBuild` destinazione principale e la destinazione dopo la destinazione. Per impostazione predefinita, le destinazioni vuote nelle destinazioni comuni non eseguono alcuna operazione, ma è possibile eseguire l'override del comportamento predefinito definendo le destinazioni desiderate in un file di progetto che importa le destinazioni comuni. Eseguendo l'override delle destinazioni predefinite, è possibile usare le attività MSBuild per offrire un maggiore controllo sul processo di compilazione.
Le destinazioni comuni contiene un set di destinazioni vuote predefinite che viene chiamato prima e dopo alcune delle destinazioni principali nel processo di compilazione. Ad esempio, MSBuild `BeforeBuild` chiama la `CoreBuild` destinazione `AfterBuild` prima della `CoreBuild` destinazione principale e la destinazione dopo la destinazione. Per impostazione predefinita, le destinazioni vuote nelle destinazioni comuni non eseguono alcuna operazione, ma è possibile eseguire l'override del comportamento predefinito definendo le destinazioni desiderate in un file di progetto che importa le destinazioni comuni. Eseguendo l'override delle destinazioni predefinite, è possibile usare le attività MSBuild per offrire un maggiore controllo sul processo di compilazione.

> [!NOTE]
> I progetti in stile SDK hanno un'importazione implicita delle destinazioni *dopo l'ultima riga del file di progetto.* Ciò significa che non è possibile eseguire l'override delle destinazioni predefinite a meno che non si specifichino manualmente le importazioni come descritto in [Procedura: utilizzare gli SDK del progetto MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Per eseguire l'override di una destinazione predefinita

1. Identificare una destinazione predefinita nelle destinazioni comuni che si desidera sostituire. Nella tabella seguente è riportato l'elenco completo delle destinazioni di cui è possibile eseguire l'override in totale sicurezza.

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

Nella tabella seguente vengono illustrate tutte le destinazioni nelle destinazioni comuni che è possibile ignorare in modo sicuro.

|Nome di destinazione|Descrizione|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il completamento della compilazione principale. La maggior parte delle personalizzazioni avviene in una di queste due destinazioni.|
|`BeforeBuild`, `AfterBuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo qualsiasi altra attività nella compilazione. **Nota:** le destinazioni `BeforeBuild` e `AfterBuild` sono già definite nei commenti alla fine della maggior parte dei file di progetto, consentendo di aggiungere facilmente eventi di pre e post-compilazione nel file di progetto.|
|`BeforeRebuild`, `AfterRebuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la ricompilazione. L'ordine di esecuzione di destinazione in `BeforeRebuild` `Clean` *Microsoft.Common.targets* è: , , `Build`e quindi `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pulitura.|
|`BeforePublish`, `AfterPublish`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pubblicazione.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la risoluzione dei riferimenti all'assembly.|
|`BeforeResGen`, `AfterResGen`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la generazione delle risorse.|

## <a name="example-aftertargets-and-beforetargets"></a>Esempio: AfterTargets e BeforeTargetsExample: AfterTargets and BeforeTargets

Nell'esempio seguente viene `AfterTargets` illustrato come utilizzare l'attributo per aggiungere una destinazione personalizzata che esegue un'operazione con i file di output. In questo caso, copia i file di output in una nuova cartella *CustomOutput*.  Nell'esempio viene inoltre illustrato come pulire i file `CustomClean` creati dall'operazione di compilazione personalizzata con una destinazione utilizzando un `BeforeTargets` attributo e specificando che l'operazione di pulizia personalizzata viene eseguita prima della `CoreClean` destinazione.

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
> Assicurarsi di utilizzare nomi diversi da quelli predefiniti elencati nella tabella nella sezione precedente `CustomAfterBuild`(ad `AfterBuild`esempio, la destinazione di compilazione personalizzata è stata denominata qui , non ), poiché tali destinazioni predefinite vengono sostituite dall'importazione SDK che le definisce. Non viene visualizzata l'importazione del file di destinazione che esegue l'override di tali destinazioni, `Sdk` ma viene aggiunto in modo implicito alla fine del file di progetto quando si utilizza il metodo di attributo per fare riferimento a un SDK.

## <a name="override-dependson-properties"></a>Eseguire l'override delle proprietà DependsOn

L'override di destinazioni predefinite è un modo semplice per estendere il processo di compilazione, ma, poiché MSBuild valuta la definizione di destinazioni in sequenza, non è possibile impedire a un altro progetto che importa il progetto di eseguire l'override delle destinazioni già disponibili Override. Di conseguenza, ad esempio, l'ultima destinazione `AfterBuild` definita nel file di progetto, al termine dell'importazione di tutti gli altri progetti, sarà quella usata durante la compilazione.

È possibile proteggersi da sostituzioni non intenzionali di destinazioni `DependsOnTargets` eseguendo l'override delle proprietà DependsOn utilizzate negli attributi in tutte le destinazioni comuni. Nella destinazione `Build`, ad esempio, il valore dell'attributo `DependsOnTargets` è `"$(BuildDependsOn)"`. Prendere in considerazione:

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

1. Identificare una proprietà DependsOn predefinita nelle destinazioni comuni di cui si desidera eseguire l'override. Nella tabella che segue è riportato un elenco delle proprietà DependsOn comunemente sottoposte a override.

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

L'esempio seguente è `BeforeTargets` `AfterTargets` simile all'esempio e , ma mostra come ottenere funzionalità simili. Estende la compilazione `BuildDependsOn` utilizzando per `CustomAfterBuild` aggiungere la propria attività che copia i file `CustomClean` di `CleanDependsOn`output dopo la compilazione e aggiunge anche l'attività corrispondente utilizzando .  

In questo esempio, si tratta di un progetto di tipo SDK. Come accennato nella nota sui progetti in stile SDK più indietro `Sdk` in questo articolo, è necessario utilizzare il metodo di importazione manuale anziché l'attributo utilizzato da Visual Studio quando genera i file di progetto.

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

L'ordine degli elementi è importante. Gli `BuildDependsOn` `CleanDependsOn` elementi e devono essere visualizzati dopo l'importazione del file targets SDK standard.

## <a name="see-also"></a>Vedere anche

- [Integrazione con Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [File .targets](../msbuild/msbuild-dot-targets-files.md)
