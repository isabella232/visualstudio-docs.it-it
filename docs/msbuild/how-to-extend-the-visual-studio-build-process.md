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
ms.openlocfilehash: cca0c55951d4928347528814d043bb8a7c55be9a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633850"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Procedura: Estendere il processo di compilazione di Visual Studio

Il processo di compilazione di Visual Studio è definito da una serie di file MSBuild *. targets* importati nel file di progetto. Uno di questi file importati, *Microsoft.Common.targets*, può essere esteso per consentire l'esecuzione di attività personalizzate in diversi punti del processo di compilazione. Questo articolo illustra due metodi che è possibile usare per estendere il processo di compilazione di Visual Studio:

- Override di destinazioni predefinite specifiche definite nelle destinazioni comuni (*Microsoft. Common. targets* o i file che importa).

- Override delle proprietà "DependsOn" definite nelle destinazioni comuni.
## <a name="override-predefined-targets"></a>Eseguire l'override di destinazioni predefinite

## <a name="override-predefined-targets"></a>Eseguire l'override di destinazioni predefinite

Le destinazioni comuni contengono un set di destinazioni vuote predefinite che vengono chiamate prima e dopo alcune delle destinazioni principali nel processo di compilazione. MSBuild, ad esempio, chiama la destinazione `BeforeBuild` prima della destinazione `CoreBuild` principale e della destinazione `AfterBuild` dopo la destinazione `CoreBuild`. Per impostazione predefinita, le destinazioni vuote nelle destinazioni comuni non eseguono alcuna operazione, ma è possibile eseguire l'override del comportamento predefinito definendo le destinazioni desiderate in un file di progetto che importa le destinazioni comuni. Eseguendo l'override delle destinazioni predefinite, è possibile usare le attività di MSBuild per fornire un maggiore controllo sul processo di compilazione.
Le destinazioni comuni contengono un set di destinazioni vuote predefinite che vengono chiamate prima e dopo alcune delle destinazioni principali nel processo di compilazione. MSBuild, ad esempio, chiama la destinazione `BeforeBuild` prima della destinazione `CoreBuild` principale e della destinazione `AfterBuild` dopo la destinazione `CoreBuild`. Per impostazione predefinita, le destinazioni vuote nelle destinazioni comuni non eseguono alcuna operazione, ma è possibile eseguire l'override del comportamento predefinito definendo le destinazioni desiderate in un file di progetto che importa le destinazioni comuni. Eseguendo l'override delle destinazioni predefinite, è possibile usare le attività di MSBuild per fornire un maggiore controllo sul processo di compilazione.

> [!NOTE]
> I progetti in stile SDK hanno un'importazione implicita di destinazioni *dopo l'ultima riga del file di progetto*. Ciò significa che non è possibile eseguire l'override delle destinazioni predefinite a meno che non si specifichino manualmente le importazioni, come descritto in [procedura: usare gli SDK di progetto MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Per eseguire l'override di una destinazione predefinita

1. Identificare una destinazione predefinita nelle destinazioni comuni di cui si vuole eseguire l'override. Nella tabella seguente è riportato l'elenco completo delle destinazioni di cui è possibile eseguire l'override in totale sicurezza.

2. Definire le destinazioni alla fine del file di progetto, immediatamente prima del tag `</Project>`. Ad esempio,

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

|Nome destinazione|Descrizione|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il completamento della compilazione principale. La maggior parte delle personalizzazioni avviene in una di queste due destinazioni.|
|`BeforeBuild`, `AfterBuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo qualsiasi altra attività nella compilazione. **Nota:** le destinazioni `BeforeBuild` e `AfterBuild` sono già definite nei commenti alla fine della maggior parte dei file di progetto, consentendo di aggiungere facilmente eventi di pre e post-compilazione nel file di progetto.|
|`BeforeRebuild`, `AfterRebuild`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la ricompilazione. L'ordine di esecuzione delle destinazioni in *Microsoft.Common.targets* è: `BeforeRebuild`, `Clean`, `Build` e quindi `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pulitura.|
|`BeforePublish`, `AfterPublish`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo il richiamo della funzionalità di base per la pubblicazione.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la risoluzione dei riferimenti all'assembly.|
|`BeforeResGen`, `AfterResGen`|Le attività inserite in una di queste destinazioni vengono eseguite prima o dopo la generazione delle risorse.|

## <a name="override-dependson-properties"></a>Eseguire l'override delle proprietà DependsOn

L'override di destinazioni predefinite è un modo semplice per estendere il processo di compilazione, ma poiché MSBuild valuta la definizione delle destinazioni in modo sequenziale, non è possibile impedire a un altro progetto che importa il progetto di eseguire l'override delle destinazioni già presenti sottoposto. Di conseguenza, ad esempio, l'ultima destinazione `AfterBuild` definita nel file di progetto, al termine dell'importazione di tutti gli altri progetti, sarà quella usata durante la compilazione.

È possibile proteggere gli override non intenzionali delle destinazioni eseguendo l'override delle proprietà DependsOn utilizzate negli attributi `DependsOnTargets` in tutte le destinazioni comuni. Nella destinazione `Build`, ad esempio, il valore dell'attributo `DependsOnTargets` è `"$(BuildDependsOn)"`. Valutare:

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

È possibile eseguire l'override di questo valore di proprietà dichiarando un'altra proprietà denominata `BuildDependsOn` alla fine del file di progetto. L'inclusione della proprietà `BuildDependsOn` precedente nella nuova proprietà consente di aggiungere nuove destinazioni all'inizio e alla fine dell'elenco di destinazioni. Ad esempio,

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

## <a name="see-also"></a>Vedere anche

- [Integrazione con Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [File con estensione targets](../msbuild/msbuild-dot-targets-files.md)
