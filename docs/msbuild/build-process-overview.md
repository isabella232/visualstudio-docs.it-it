---
title: Come vengono compilati i progetti in MSBuild
description: Informazioni sul modo in cui MSBuild elabora i file di progetto, se richiamati da Visual Studio o da una riga di comando o uno script.
ms.custom: SEO-VS-2020
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4374e6763933e2da3e6a11c5609b76e3341e1050
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353252"
---
# <a name="how-msbuild-builds-projects"></a>Come vengono compilati i progetti in MSBuild

In che modo MSBuild funziona effettivamente? In questo articolo si apprenderà come MSBuild elabora i file di progetto, se richiamati da Visual Studio o da una riga di comando o uno script. Sapere come funziona MSBuild può aiutarti a diagnosticare meglio i problemi e a personalizzare meglio il processo di compilazione. Questo articolo descrive il processo di compilazione ed è ampiamente applicabile a tutti i tipi di progetto.

Il processo di compilazione completo è costituito dall' [avvio iniziale](#startup), dalla [valutazione](#evaluation-phase)e dall' [esecuzione](#execution-phase) delle destinazioni e delle attività che compilano il progetto. Oltre a questi input, le importazioni esterne definiscono i dettagli del processo di compilazione, incluse le [importazioni standard](#standard-imports) , ad esempio *Microsoft. Common. targets* e le [importazioni configurabili dall'utente](#user-configurable-imports) a livello di soluzione o di progetto.

## <a name="startup"></a>Avvio

MSBuild può essere richiamato da Visual Studio tramite il modello a oggetti MSBuild in *Microsoft.Build.dll*oppure richiamando il file eseguibile direttamente nella riga di comando o in uno script, ad esempio nei sistemi ci. In entrambi i casi, gli input che interessano il processo di compilazione includono il file di progetto (o l'oggetto di progetto interno a Visual Studio), possibilmente un file di soluzione, le variabili di ambiente e le opzioni della riga di comando o gli equivalenti del modello a oggetti. Durante la fase di avvio, le opzioni della riga di comando o gli equivalenti del modello a oggetti vengono usati per configurare le impostazioni di MSBuild, ad esempio la configurazione dei logger. Le proprietà impostate nella riga di comando usando `-property` l' `-p` opzione o sono impostate come proprietà globali, che eseguono l'override di tutti i valori che verrebbero impostati nei file di progetto, anche se i file di progetto vengono letti in un secondo momento.

Le sezioni successive sono relative ai file di input, ad esempio i file di soluzione o di progetto.

### <a name="solutions-and-projects"></a>Soluzioni e progetti

Le istanze di MSBuild possono essere costituite da un progetto o da molti progetti come parte di una soluzione. Il file di soluzione non è un file XML di MSBuild, ma viene interpretato da MSBuild per conoscerli tutti i progetti che devono essere compilati per le impostazioni di configurazione e piattaforma specificate. Quando MSBuild elabora questo input XML, viene definito compilazione della soluzione. Dispone di alcuni punti estensibili che consentono di eseguire un elemento a ogni compilazione della soluzione, ma poiché questa build è un'esecuzione separata dalle compilazioni di singoli progetti, nessuna impostazione delle proprietà o delle definizioni di destinazione della compilazione della soluzione è pertinente per ogni compilazione di progetto.

Per informazioni su come estendere la compilazione della soluzione, vedere [personalizzare la compilazione della soluzione](customize-your-build.md#customize-the-solution-build).

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Compilazioni di Visual Studio e MSBuild.exe compilazioni

Esistono differenze significative tra il momento in cui i progetti vengono compilati in Visual Studio e quando si richiama direttamente MSBuild, tramite il file eseguibile di MSBuild o quando si usa il modello a oggetti MSBuild per avviare una compilazione. Visual Studio gestisce l'ordine di compilazione del progetto per le compilazioni di Visual Studio. chiama solo MSBuild a livello di singolo progetto e, in questo caso, vengono impostate due proprietà booleane ( `BuildingInsideVisualStudio` , `BuildProjectReferences` ) che influiscono in modo significativo sulle operazioni eseguite da MSBuild. All'interno di ogni progetto, l'esecuzione viene eseguita allo stesso modo di quando viene richiamata tramite MSBuild, ma la differenza si verifica con i progetti a cui si fa riferimento. In MSBuild, quando i progetti a cui si fa riferimento sono obbligatori, viene effettivamente eseguita una compilazione. ovvero esegue attività e strumenti e genera l'output. Quando una compilazione di Visual Studio trova un progetto a cui si fa riferimento, MSBuild restituisce solo gli output previsti dal progetto a cui si fa riferimento. consente a Visual Studio di controllare la compilazione degli altri progetti. In Visual Studio viene determinato l'ordine di compilazione e le chiamate a MSBuild separatamente (in base alle esigenze), completamente sotto il controllo di Visual Studio.

Un'altra differenza si verifica quando MSBuild viene richiamato con un file di soluzione, MSBuild analizza il file di soluzione, crea un file di input XML standard, lo valuta e lo esegue come progetto. La compilazione della soluzione viene eseguita prima di qualsiasi progetto. Quando si esegue la compilazione da Visual Studio, non si verifica alcuna situazione. MSBuild non visualizza mai il file della soluzione. Di conseguenza, la personalizzazione della compilazione della soluzione (usando *before). SolutionName. sln. targets* e *after. SolutionName. sln. targets*) si applica solo ai MSBuild.exe o basati sul modello a oggetti, non sulle compilazioni di Visual Studio.

### <a name="project-sdks"></a>SDK per i progetti

La funzionalità SDK per i file di progetto MSBuild è relativamente nuova. Prima di questa modifica, i file di progetto importavano in modo esplicito i file *. targets* e *. props* che definiscono il processo di compilazione per un determinato tipo di progetto.

I progetti .NET Core importano la versione di .NET SDK appropriata. Vedere Panoramica, [SDK del progetto .NET Core](/dotnet/core/project-sdk/overview)e riferimento alle [Proprietà](/dotnet/core/project-sdk/msbuild-props).

## <a name="evaluation-phase"></a>Fase di valutazione

In questa sezione viene illustrato il modo in cui questi file di input vengono elaborati e analizzati per produrre oggetti in memoria che determinano gli elementi che verranno compilati.

Lo scopo della fase di valutazione è creare le strutture degli oggetti in memoria in base ai file XML di input e all'ambiente locale. La fase di valutazione è costituita da sei passaggi che elaborano i file di input, ad esempio i file XML del progetto o, e i file XML importati, in genere denominati file con *estensione Props* o *targets* , a seconda che impostino principalmente proprietà o definiscano le destinazioni di compilazione. Ogni passaggio compila una parte degli oggetti in memoria che vengono successivamente utilizzati nella fase di esecuzione per compilare i progetti, ma durante la fase di valutazione non si verificano azioni di compilazione effettive. All'interno di ogni passaggio, gli elementi vengono elaborati nell'ordine in cui vengono visualizzati.

I passaggi della fase di valutazione sono i seguenti:

- Valutazione delle variabili di ambiente
- Valutare le importazioni e le proprietà
- Valutare le definizioni degli elementi
- Valuta elementi
- Valuta elementi [UsingTask](usingtask-element-msbuild.md)
- Valuta destinazioni

L'ordine di questi passaggi presenta implicazioni significative ed è importante da tenere presente quando si Personalizza il file di progetto. Vedere l' [ordine di valutazione delle proprietà e degli elementi](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Valutazione delle variabili di ambiente

In questa fase, le variabili di ambiente vengono usate per impostare proprietà equivalenti. La variabile di ambiente PATH, ad esempio, viene resa disponibile come proprietà `$(PATH)` . Quando viene eseguito dalla riga di comando o da uno script, l'ambiente di comando viene usato come di consueto e, quando viene eseguito da Visual Studio, viene usato l'ambiente attivo quando viene avviato Visual Studio.

### <a name="evaluate-imports-and-properties"></a>Valutare le importazioni e le proprietà

In questa fase viene letto l'intero codice XML di input, inclusi i file di progetto e l'intera catena di importazioni. MSBuild crea una struttura XML in memoria che rappresenta l'XML del progetto e tutti i file importati. Al momento, le proprietà non incluse nelle destinazioni vengono valutate e impostate.

Come conseguenza di MSBuild che legge tutti i file di input XML all'inizio del processo, qualsiasi modifica apportata a tali input durante il processo di compilazione non influisce sulla compilazione corrente.

Le proprietà esterne a qualsiasi destinazione sono gestite in modo diverso rispetto alle proprietà all'interno di destinazioni. In questa fase vengono valutate solo le proprietà definite all'esterno di qualsiasi destinazione.

Poiché le proprietà vengono elaborate in ordine nel passaggio delle proprietà, una proprietà in un punto qualsiasi dell'input può accedere ai valori delle proprietà visualizzati in precedenza nell'input, ma non alle proprietà visualizzate in un secondo momento.

Poiché le proprietà vengono elaborate prima della valutazione degli elementi, non è possibile accedere al valore di qualsiasi elemento durante una parte del passaggio delle proprietà. 

### <a name="evaluate-item-definitions"></a>Valutare le definizioni degli elementi

In questa fase, le [definizioni degli elementi](item-definitions.md) vengono interpretate e viene creata una rappresentazione in memoria di queste definizioni.

### <a name="evaluate-items"></a>Valuta elementi

Gli elementi definiti all'interno di una destinazione vengono gestiti in modo diverso dagli elementi esterni a qualsiasi destinazione. In questa fase vengono elaborati gli elementi esterni a qualsiasi destinazione e i relativi metadati associati.  I metadati impostati per definizione di elemento vengono sottoposti a override dall'impostazione dei metadati per gli elementi. Poiché gli elementi vengono elaborati nell'ordine in cui sono visualizzati, è possibile fare riferimento a elementi definiti in precedenza, ma non a quelli visualizzati in un secondo momento. Poiché gli elementi passano dopo il passaggio delle proprietà, gli elementi possono accedere a qualsiasi proprietà se definito al di fuori di tutte le destinazioni, indipendentemente dal fatto che la definizione di proprietà venga visualizzata in un secondo momento.

### <a name="evaluate-usingtask-elements"></a>Valuta `UsingTask` elementi

In questa fase vengono letti gli elementi [UsingTask](usingtask-element-msbuild.md) e le attività vengono dichiarate per un uso successivo durante la fase di esecuzione.

### <a name="evaluate-targets"></a>Valuta destinazioni

In questa fase, tutte le strutture degli oggetti di destinazione vengono create in memoria, in preparazione per l'esecuzione. Non si verifica alcuna esecuzione effettiva. 

## <a name="execution-phase"></a>Fase di esecuzione

Nella fase di esecuzione, le destinazioni vengono ordinate ed eseguite e tutte le attività vengono eseguite. Prima di tutto, le proprietà e gli elementi definiti all'interno di destinazioni vengono valutati insieme in una singola fase nell'ordine in cui sono visualizzati. L'ordine di elaborazione è in particolare diverso da quello in cui vengono elaborate le proprietà e gli elementi che non sono in una destinazione: tutte le proprietà e quindi tutti gli elementi, in sessioni separate. Le modifiche apportate alle proprietà e agli elementi all'interno di una destinazione possono essere osservate dopo la destinazione in cui sono state modificate.

### <a name="target-build-order"></a>Ordine di compilazione delle destinazioni

In un singolo progetto le destinazioni vengono eseguite in modo seriale. Il problema centrale è la modalità di determinazione dell'ordine di compilazione di tutti gli elementi in, in modo che le dipendenze vengano utilizzate per compilare le destinazioni nell'ordine corretto.  

L'ordine di compilazione di destinazione è determinato dall'utilizzo degli `BeforeTargets` `DependsOnTargets` attributi, e `AfterTargets` in ogni destinazione. L'ordine delle destinazioni successive può essere influenzato durante l'esecuzione di una destinazione precedente se la destinazione precedente modifica una proprietà a cui si fa riferimento in questi attributi.

Le regole per l'ordinamento sono descritte in [determinare l'ordine di compilazione di destinazione](target-build-order.md#determine-the-target-build-order). Il processo è determinato da una struttura dello stack contenente le destinazioni da compilare. La destinazione all'inizio di questa attività avvia l'esecuzione e, se dipende da qualsiasi altra, le destinazioni vengono inserite nella parte superiore dello stack e avviano l'esecuzione.  Quando è presente una destinazione senza dipendenze, viene eseguita fino al completamento e la destinazione padre riprende.

### <a name="project-references"></a>Riferimenti al progetto

MSBuild può assumere due percorsi di codice, quello normale, qui descritto e l'opzione Graph descritta nella sezione successiva.

I singoli progetti specificano la dipendenza da altri progetti tramite `ProjectReference` gli elementi. Quando inizia la compilazione di un progetto nella parte superiore dello stack, raggiunge il punto in cui `ResolveProjectReferences` viene eseguita la destinazione, una destinazione standard definita nei file di destinazione comuni.

`ResolveProjectReferences` richiama l'attività MSBuild con gli input degli `ProjectReference` elementi per ottenere gli output. Gli `ProjectReference` elementi vengono trasformati in elementi locali, ad esempio `Reference` . La fase di esecuzione di MSBuild per il progetto corrente viene sospesa mentre la fase di esecuzione inizia a elaborare il progetto a cui si fa riferimento (la fase di valutazione viene eseguita prima in base alle esigenze). Il progetto a cui si fa riferimento viene compilato solo dopo aver iniziato a compilare il progetto dipendente, quindi viene creato un albero di progetti che compilano.

Visual Studio consente di creare dipendenze del progetto nei file di soluzione (con estensione sln). Le dipendenze vengono specificate nel file della soluzione e vengono rispettate solo quando si compila una soluzione o quando si compila in Visual Studio. Se si compila un singolo progetto, questo tipo di dipendenza viene ignorato. I riferimenti alla soluzione vengono trasformati da MSBuild in `ProjectReference` elementi e successivamente vengono trattati nello stesso modo.

### <a name="graph-option"></a>Opzione Graph

Se si specifica l'opzione di compilazione Graph ( `-graphBuild` o `-graph` ), `ProjectReference` diventa un concetto di prima classe utilizzato da MSBuild. MSBuild analizzerà tutti i progetti e creerà il grafico dell'ordine di compilazione, un grafico delle dipendenze effettivo dei progetti, che viene quindi attraversato per determinare l'ordine di compilazione. Come per le destinazioni nei singoli progetti, MSBuild assicura che i progetti a cui si fa riferimento vengano compilati dopo i progetti da cui dipendono.

## <a name="parallel-execution"></a>Esecuzione parallela

Se si usa il supporto multiprocessore ( `-maxCpuCount` o `-m` Switch), MSBuild crea nodi, ovvero processi MSBuild che usano i core CPU disponibili. Ogni progetto viene inviato a un nodo disponibile. All'interno di un nodo, le compilazioni di singoli progetti vengono eseguite in modo seriale

Le attività possono essere abilitate per l'esecuzione parallela impostando una variabile booleana <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> , che viene impostata in base al valore della `$(BuildInParallel)` Proprietà in MSBuild. Per le attività abilitate per l'esecuzione parallela, un'utilità di pianificazione del lavoro gestisce i nodi e assegna il lavoro ai nodi.

Vedere [compilazione di più progetti in parallelo con MSBuild](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>Importazioni standard

*Microsoft. Common. props* e *Microsoft. Common. targets* sono entrambi importati dai file di progetto .NET (in modo esplicito o implicito nei progetti in stile SDK) e si trovano nella cartella *MSBuild\Current\bin* in un'installazione di Visual Studio. I progetti C++ hanno una propria gerarchia di importazioni. vedere elementi [interni MSBuild per progetti C++](/cpp/build/reference/msbuild-visual-cpp-overview).

Il file *Microsoft. Common. props* imposta le impostazioni predefinite di cui è possibile eseguire l'override. Viene importato (in modo esplicito o implicito) all'inizio di un file di progetto. In questo modo, le impostazioni del progetto vengono visualizzate dopo le impostazioni predefinite, in modo da eseguirne l'override.

Il file *Microsoft. Common. targets* e i file di destinazione importati definiscono il processo di compilazione standard per i progetti .NET. Fornisce anche punti di estensione che è possibile usare per personalizzare la compilazione.

Nell'implementazione *Microsoft. Common. targets* è un thin wrapper che importa *Microsoft. Common. CurrentVersion. targets*. Questo file contiene le impostazioni per le proprietà standard e definisce le destinazioni effettive che definiscono il processo di compilazione. La `Build` destinazione è definita qui, ma in realtà è vuota. Tuttavia, la `Build` destinazione contiene l' `DependsOn` attributo che specifica le singole destinazioni che costituiscono i passaggi di compilazione effettivi, ovvero `BeforeBuild` , `CoreBuild` e `AfterBuild` . La `Build` destinazione è definita come segue:

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild` e `AfterBuild` sono punti di estensione. Sono vuoti nel file *Microsoft. Common. CurrentVersion. targets* , ma i progetti possono fornire le proprie `BeforeBuild` destinazioni e le proprie `AfterBuild` destinazioni con le attività che devono essere eseguite prima o dopo il processo di compilazione principale. `AfterBuild` viene eseguito prima della destinazione no-op, `Build` , perché `AfterBuild` viene visualizzato nell' `DependsOn` attributo nella `Build` destinazione, ma si verifica dopo `CoreBuild` .

La `CoreBuild` destinazione contiene le chiamate agli strumenti di compilazione, come indicato di seguito:

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

Nella tabella seguente vengono descritte queste destinazioni. alcune destinazioni sono applicabili solo a determinati tipi di progetto.

| Destinazione | Descrizione |
|--------|-------------|
| BuildOnlySettings | Impostazioni solo per le compilazioni reali, non per quando MSBuild viene richiamato durante il caricamento del progetto da Visual Studio. |
| PrepareForBuild | Preparare i prerequisiti per la compilazione |
| PreBuildEvent | Punto di estensione per i progetti che definiscono le attività da eseguire prima della compilazione |
| ResolveProjectReferences | Analizzare le dipendenze del progetto e creare progetti a cui si fa riferimento |
| ResolveAssemblyReferences| Individuare gli assembly a cui si fa riferimento. |
| ResolveReferences | È costituito da `ResolveProjectReferences` e `ResolveAssemblyReferences` per individuare tutte le dipendenze |
| PrepareResources | Elabora file di risorse |
| ResolveKeySource| Risolvere la chiave con nome sicuro usata per firmare l'assembly e il certificato usato per firmare i manifesti [ClickOnce](../deployment/clickonce-security-and-deployment.md) . |
| Compilazione | Richiama il compilatore |
| ExportWindowsMDFile | Genera un file [WinMD](/uwp/winrt-cref/winmd-files) dai file WinMDModule generati dal compilatore. |
| UnmanagedUnregistration | Rimuovere/pulire le voci del registro di sistema di [interoperabilità COM](/dotnet/standard/native-interop/cominterop) da una compilazione precedente |
| GenerateSerializationAssemblies | Generare un assembly di serializzazione XML utilizzando [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe).|
| CreateSatelliteAssemblies | Creare un assembly satellite per ogni lingua univoca nelle risorse. |
| Genera manifesti | Genera manifesti di applicazione e distribuzione [ClickOnce](../deployment/clickonce-security-and-deployment.md) o un manifesto nativo. |
| GetTargetPath | Restituisce un elemento contenente il prodotto di compilazione (eseguibile o assembly) per il progetto, con i metadati. |
| PrepareForRun | Copiare gli output di compilazione nella directory finale se sono stati modificati. |
| UnmanagedRegistration | Imposta voci del registro di sistema per l' [interoperabilità COM](/dotnet/standard/native-interop/cominterop) |
| IncrementalClean | Rimuovere i file che sono stati generati in una compilazione precedente ma che non sono stati generati nella compilazione corrente. Questa operazione è necessaria per eseguire `Clean` operazioni nelle compilazioni incrementali. |
| PostBuildEvent | Punto di estensione per i progetti che definiscono le attività da eseguire dopo la compilazione |

Molte delle destinazioni della tabella precedente si trovano in importazioni specifiche del linguaggio, ad esempio *Microsoft. CSharp. targets*. Questo file definisce i passaggi nel processo di compilazione standard specifico per i progetti C# .NET. Ad esempio, contiene la `Compile` destinazione che chiama effettivamente il compilatore C#.

## <a name="user-configurable-imports"></a>Importazioni configurabili dall'utente

Oltre alle importazioni standard, è possibile aggiungere diverse importazioni per personalizzare il processo di compilazione.

- *Directory. Build. props*
- *Directory.Build.targets*

Questi file vengono letti dalle importazioni standard per tutti i progetti in qualsiasi sottocartella. Questo è in genere a livello di soluzione per le impostazioni per controllare tutti i progetti nella soluzione, ma potrebbe anche essere più alto nel file System, fino alla radice dell'unità.

Il file *Directory. Build. props* viene importato da *Microsoft. Common. props*, quindi le proprietà definite in essi sono disponibili nel file di progetto. Possono essere ridefiniti nel file di progetto per personalizzare i valori in base al progetto. Il file *Directory. Build. targets* viene letto dopo il file di progetto. Contiene in genere le destinazioni, ma qui è anche possibile definire le proprietà che non si vuole ridefinire i singoli progetti.

## <a name="customizations-in-a-project-file"></a>Personalizzazioni in un file di progetto

Visual Studio aggiorna i file di progetto quando si apportano modifiche in **Esplora soluzioni**, nella finestra **Proprietà** o nelle **proprietà del progetto**, ma è anche possibile apportare modifiche personalizzate modificando direttamente il file di progetto.

Molti comportamenti di compilazione possono essere configurati impostando le proprietà MSBuild nel file di progetto per le impostazioni locali di un progetto o come indicato nella sezione precedente, creando un file *Directory. Build. props* per impostare le proprietà a livello globale per intere cartelle di progetti e soluzioni. Per le compilazioni ad hoc nella riga di comando o negli script, è anche possibile usare l' `/p` opzione nella riga di comando per impostare le proprietà di una chiamata specifica di MSBuild. Per informazioni sulle proprietà che è possibile impostare, vedere [Proprietà comuni del progetto MSBuild](common-msbuild-project-properties.md) .

## <a name="next-steps"></a>Passaggi successivi

Il processo MSBuild presenta diversi altri punti di estensione diversi da quelli descritti qui. Vedere [personalizzare la compilazione](customize-your-build.md). e [come estendere il processo di compilazione di Visual Studio](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Vedere anche

[MSBuild](msbuild.md)
