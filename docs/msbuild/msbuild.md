---
title: MSBuild | Microsoft Docs
description: Informazioni su come la piattaforma Microsoft Build Engine (MSBuild) fornisce un file di progetto con un XML Schema per controllare le compilazioni.
ms.custom: SEO-VS-2020
ms.date: 08/11/2021
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b9e2e3acd40bb5a5b7f45b636b3539b5c24f7f29
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108486"
---
# <a name="msbuild"></a>MSBuild

Il Microsoft Build Engine è una piattaforma per la compilazione di applicazioni. Questo motore, anche noto come MSBuild, fornisce un XML Schema per un file di progetto che controlla il modo in cui la piattaforma di compilazione elabora e compila il software. Visual Studio usa MSBuild, ma MSBuild non dipende da Visual Studio. Richiamando *msbuild.exe* nel file di progetto o di soluzione, è possibile orchestrare e compilare prodotti in ambienti in Visual Studio non è installato.

 Visual Studio utilizza MSBuild per caricare e compilare progetti gestiti. I file di progetto in Visual Studio (con estensione *csproj*, *vbproj*, *vcxproj* e altre) contengono il codice XML di MSBuild che viene eseguito quando si compila un progetto usando l'IDE. I progetti di Visual Studio importano tutte le impostazioni e tutti i processi di compilazione necessari per eseguire il normale lavoro di sviluppo standard, ma è possibile estenderli o modificarli in Visual Studio o mediante un editor XML.

 Per informazioni sulle MSBuild per C++, [vedere MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Gli esempi seguenti illustrano quando è possibile eseguire compilazioni richiamando MSBuild dalla riga di comando anziché dall'IDE Visual Studio.

- Visual Studio non è installato. (Scaricare[MSBuild senza Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- Si desidera usare la versione a 64 bit di MSBuild. Questa versione di MSBuild non è solitamente necessaria, ma consente l'accesso di MSBuild a una maggiore quantità di memoria.

- Si desidera eseguire una compilazione in più processi. Tuttavia, è possibile usare l'IDE per ottenere lo stesso risultato nei progetti di C++ e C#.

- Si intende modificare il sistema di compilazione. Ad esempio, può essere necessario consentire le azioni seguenti:

  - Pre-elabora i file prima che arrivino al compilatore.

  - Copiare gli output di compilazione in un'altra posizione.

  - Creare file compressi dagli output di compilazione.

  - Eseguire un passaggio di post-elaborazione. Ad esempio, può essere utile contrassegnare un assembly con una versione diversa.

È possibile scrivere codice nell'IDE di Visual Studio ed eseguire le compilazioni tramite MSBuild. In alternativa, è possibile compilare codice nell'IDE in un computer di sviluppo, ma eseguire MSBuild dalla riga di comando per compilare codice integrato da più sviluppatori. È anche possibile usare l'interfaccia della riga di comando [di .NET Core,](/dotnet/core/tools/)che usa MSBuild, per compilare progetti .NET Core.

> [!NOTE]
> È possibile usare Azure Pipelines per compilare, testare e distribuire automaticamente l'applicazione. Il sistema di compilazione può eseguire le compilazioni automaticamente quando gli sviluppatori archiviano il codice, ad esempio come parte di una strategia di integrazione continuata, o secondo a una pianificazione, ad esempio una compilazione notturna di test di verifica compilazione. Azure Pipelines compila il codice usando MSBuild. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Questo articolo offre una panoramica delle MSBuild. Per un'esercitazione introduttiva, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Uso di MSBuild al prompt dei comandi

 Per eseguire MSBuild prompt dei comandi, passare un file di progetto *aMSBuild.exe*, insieme alle opzioni della riga di comando appropriate. Le opzioni della riga di comando consentono di impostare proprietà, eseguire destinazioni specifiche e impostare altre opzioni che controllano il processo di compilazione. Ad esempio, per compilare il file *MyProj.proj* con la proprietà `Configuration` impostata su `Debug` si usa la sintassi della riga di comando seguente.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Per altre informazioni sulle opzioni MSBuild riga di comando, vedere [Riferimenti alla riga di comando.](../msbuild/msbuild-command-line-reference.md)

> [!IMPORTANT]
> Prima di scaricare un progetto, determinare l'attendibilità del codice.

## <a name="project-file"></a>File di progetto

 MSBuild usa un formato di file di progetto basato su XML semplice ed estendibile. Il MSBuild di file di progetto consente agli sviluppatori di descrivere gli elementi da determinare e come devono essere compilati per diversi sistemi operativi e configurazioni. Gli sviluppatori hanno inoltre la possibilità di creare regole di compilazione riutilizzabili che possono essere organizzate in file separati. Ciò consente di eseguire in modo coerente le compilazioni relative ai vari progetti del prodotto.

 Il Visual Studio di compilazione archivia la logica specifica del progetto nel file di progetto stesso e usa i file XML MSBuild importati con estensioni come *props* e *targets* per definire la logica di compilazione standard. I *file props* definiscono le MSBuild e i file con estensione *targets* MSBuild destinazioni. Queste importazioni sono a volte visibili nel file di progetto Visual Studio, ma nei progetti più nuovi, ad esempio i progetti .NET Core, .NET 5 e .NET 6, le importazioni non sono visibili nel file di progetto. viene invece visualizzato un riferimento all'SDK. Questi progetti sono denominati progetti di tipo SDK. Quando si fa riferimento a un SDK come .NET SDK, le importazioni di file con estensione props e target vengono specificate in modo implicito dall'SDK.

 Le sezioni seguenti descrivono alcuni degli elementi di base del formato MSBuild file di progetto. Per un'esercitazione su come creare un file di progetto di base, vedere Procedura dettagliata: Creazione di MSBuild file di [progetto da zero.](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

### <a name="properties"></a><a name="BKMK_Properties"></a> Proprietà

 Le proprietà sono coppie di chiave/valore che possono essere usate per configurare le compilazioni. Per dichiarare le proprietà, è necessario creare un elemento con lo stesso nome della proprietà, come figlio di un elemento [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Tramite il codice seguente, ad esempio, viene creata una proprietà denominata `BuildDir` con un valore `Build`.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 È possibile definire una proprietà in modo condizionale aggiungendo un attributo `Condition` nell'elemento. Il contenuto degli elementi condizionali viene elaborato solo se la condizione risulta essere `true`. Nell'esempio seguente viene definito l'elemento `Configuration`, se non è stato ancora definito.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 È possibile fare riferimento alle proprietà in tutto il file di progetto usando la sintassi $( \<PropertyName> ). È possibile, ad esempio, fare riferimento alle proprietà degli esempi precedenti usando `$(BuildDir)` e `$(Configuration)`.

 Per altre informazioni sulle proprietà, vedere [Proprietà di MSBuild](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Elementi

 Gli elementi sono input nel sistema di compilazione e, in genere, rappresentano i file. Gli elementi vengono raggruppati in tipi di elemento in base ai nomi di elemento definiti dall'utente. Tali tipi di elemento possono essere usati come parametri per le attività, le quali a loro volta utilizzano i singoli elementi dei tipi per eseguire i passaggi del processo di compilazione.

 Per dichiarare gli elementi nel file di progetto è necessario creare, come figlio di un elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md), un elemento con lo stesso nome del tipo di elemento. Ad esempio, il codice seguente crea un tipo di elemento denominato `Compile` che include due file.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 È possibile fare riferimento ai tipi di elemento in tutto il file di progetto usando la sintassi @( \<ItemType> ). Ad esempio, per fare riferimento al tipo di elemento dell'esempio si utilizza la sintassi `@(Compile)`.

 In MSBuild, i nomi di elementi e attributi prevedono la distinzione tra maiuscole e minuscole. I nomi di proprietà, elementi e metadati, invece, non prevedono tale distinzione. Nell'esempio seguente viene creato il tipo di elemento `Compile`, `comPile` o con qualsiasi altra variazione di maiuscole o minuscole e viene assegnato a esso il valore "one.cs;two.cs".

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Gli elementi possono essere dichiarati usando caratteri jolly e, negli scenari di compilazione più avanzati, possono contenere metadati aggiuntivi. Per altre informazioni sugli elementi, vedere [Elementi](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Attività

 Le attività sono unità di codice eseguibile che MSBuild progetti usano per eseguire operazioni di compilazione. Ad esempio, un'attività potrebbe compilare file di input o eseguire uno strumento esterno. Le attività possono essere riutilizzate e condivise da sviluppatori diversi in progetti diversi.

 La logica di esecuzione di un'attività viene scritta in codice gestito ed è mappata a MSBuild usando [l'elemento UsingTask.](../msbuild/usingtask-element-msbuild.md) Per scrivere un'attività personalizzata, è sufficiente creare un tipo gestito che implementi l'interfaccia <xref:Microsoft.Build.Framework.ITask>. Per altre informazioni su come scrivere attività, vedere Scrittura [di attività.](../msbuild/task-writing.md)

 MSBuild include attività comuni che è possibile modificare in base alle esigenze. Alcuni esempi sono [Copy](../msbuild/copy-task.md) per eseguire la copia dei file, [MakeDir](../msbuild/makedir-task.md) per creare le directory e [Csc](../msbuild/csc-task.md) per compilare i file di codice sorgente di Visual C#. Per un elenco delle attività disponibili insieme alle informazioni sull'utilizzo, vedere [Informazioni di riferimento sulle attività.](../msbuild/msbuild-task-reference.md)

 Un'attività viene eseguita in MSBuild file di progetto creando un elemento con il nome dell'attività come figlio di un [elemento Target.](../msbuild/target-element-msbuild.md) In genere le attività accettano parametri che vengono passati come attributi dell'elemento. Sia MSBuild proprietà che gli elementi possono essere usati come parametri. Ad esempio, il codice seguente chiama l'attività [MakeDir](../msbuild/makedir-task.md) e le passa il valore della proprietà `BuildDir` dichiarata nell'esempio precedente.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Per altre informazioni sulle attività, vedere [Attività](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a> Obiettivi

 Le destinazioni raggruppano le attività in un determinato ordine ed espongono le sezioni del file di progetto come punti di ingresso al processo di compilazione. Le destinazioni vengono spesso raggruppate in sezioni logiche per garantire una maggiore leggibilità e consentire l'espansione. La suddivisione delle istruzioni di compilazione in più destinazioni consente di chiamare una parte del processo di compilazione da altre destinazioni senza dover copiare la corrispondente sezione di codice in ognuna di esse. Ad esempio, se alcuni punti di ingresso al processo di compilazione richiedono la compilazione di riferimenti, è possibile creare una destinazione che compila riferimenti e quindi eseguire tale destinazione da ognuno dei suddetti punti di ingresso.

 Per dichiarare una destinazione nel file di progetto si usa l'elemento [Target](../msbuild/target-element-msbuild.md). Il codice seguente crea ad esempio una destinazione denominata `Compile`, che a sua volta chiama l'attività [Csc](../msbuild/csc-task.md) con l'elenco di elementi dichiarato nell'esempio precedente.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Negli scenari più avanzati, è possibile usare le destinazioni per descrivere relazioni reciproche ed eseguire analisi delle dipendenze, così da poter ignorare intere sezioni del processo di compilazione per le destinazioni che risultano essere già aggiornate. Per altre informazioni sulle destinazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Log di compilazione

 È possibile registrare errori di compilazione, avvisi e messaggi sulla console o in un altro dispositivo di output. Per altre informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md) e Registrazione in [MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Uso di MSBuild in Visual Studio

 Visual Studio usa il formato MSBuild file di progetto per archiviare le informazioni di compilazione sui progetti gestiti. Project le impostazioni aggiunte o modificate tramite l'interfaccia Visual Studio vengono riflesse in *. \* File proj* generato per ogni progetto. Visual Studio usa un'istanza ospitata di MSBuild per compilare progetti gestiti. Ciò significa che un progetto gestito può essere compilato in Visual Studio o al prompt dei comandi (anche se Visual Studio non è installato) e i risultati saranno identici.

 Per un'esercitazione sull'uso di MSBuild in Visual Studio, vedere [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Multitargeting

 Usando Visual Studio, è possibile compilare un'applicazione per l'esecuzione in una delle diverse versioni di .NET Framework. Ad esempio, è possibile compilare un'applicazione da eseguire in .NET Framework 2.0 in una piattaforma a 32 bit ed è possibile compilare la stessa applicazione per l'esecuzione in .NET Framework 4.5 in una piattaforma a 64 bit. La possibilità di compilare in più framework è denominata multitargeting.

 Di seguito sono riportati alcuni dei vantaggi del multitargeting:

- È possibile sviluppare applicazioni che hanno come destinazione versioni precedenti di .NET Framework, ad esempio le versioni 3.5 e 4.7.2.

- L'applicazione può essere destinata a un *profilo del framework*, vale a dire un subset predefinito di un framework di destinazione.

- Se viene rilasciato un Service Pack per la versione corrente .NET Framework, è possibile scegliere come destinazione.

- Il multitargeting garantisce che un'applicazione utilizzi solo le funzionalità disponibili nel framework e nella piattaforma di destinazione.

Per altre informazioni, vedere [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Vedi anche

| Titolo | Descrizione |
| - | - |
| [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Mostra come creare in modo incrementale un file di progetto di base usando soltanto un editor di testo. |
| [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md) | Introduce i blocchi predefiniti di MSBuild e mostra come scrivere, modificare ed eseguire il debug di progetti MSBuild senza chiudere l'IDE di Visual Studio. |
| [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md) | Presenta i quattro blocchi predefiniti di MSBuild: proprietà, elementi, destinazioni e attività. |
| [Elementi](../msbuild/msbuild-items.md) | Vengono descritti i concetti generali alla base del formato MSBuild file e il modo in cui le parti si uniscono. |
| [proprietà di MSBuild](../msbuild/msbuild-properties.md) | Introduce proprietà e raccolte di proprietà. Le proprietà sono coppie di chiave/valore che possono essere usate per configurare le compilazioni |
| [Server di destinazione](../msbuild/msbuild-targets.md) | Spiega come raggruppare le attività in un dato ordine e consentire che determinate sezioni del processo di compilazione vengano richiamate dalla riga di comando. |
| [Attività](../msbuild/msbuild-tasks.md) | Viene illustrato come creare un'unità di codice eseguibile che può essere usata dal MSBuild per eseguire operazioni di compilazione atomica. |
| [Condizioni](../msbuild/msbuild-conditions.md) | Descrive come usare l'attributo `Condition` in un elemento MSBuild. |
| [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md) | Illustra la suddivisione in batch, l'esecuzione di trasformazioni, il multitargeting e altre tecniche avanzate. |
| [Registrazione a MSBuild](../msbuild/logging-in-msbuild.md) | Descrive come registrare eventi, messaggi ed errori. |
| [Come vengono compilati i progetti in MSBuild](build-process-overview.md) | Descrive il processo di compilazione interno usato all'interno MSBuild |
| [Risorse aggiuntive](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Elenca risorse della community e di supporto che consentono di ottenere altre informazioni su MSBuild. |

## <a name="reference"></a>Riferimento

- [MSBuild riferimento](../msbuild/msbuild-reference.md)\
 Collegamenti ad argomenti che contengono informazioni di riferimento.

- [Glossario](msbuild-glossary.md)\
 Definisce termini comuni di MSBuild.
