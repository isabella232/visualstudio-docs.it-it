---
title: Come vengono compilati i progetti in MSBuild
description: Informazioni su come MSBuild i file di progetto, sia che siano richiamati da Visual Studio o da una riga di comando o da uno script.
ms.custom: SEO-VS-2020
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ad648b114ffd067ef1ab5d9a0ea1671d03207396
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077712"
---
# <a name="how-msbuild-builds-projects"></a>Come vengono compilati i progetti in MSBuild

Come funziona MSBuild? In questo articolo si apprenderà come MSBuild i file di progetto, sia richiamati da Visual Studio o da una riga di comando o uno script. Conoscere il MSBuild può aiutare a diagnosticare meglio i problemi e a personalizzare meglio il processo di compilazione. Questo articolo descrive il processo di compilazione ed è in gran parte applicabile a tutti i tipi di progetto.

Il processo di compilazione completo è costituito [dall'avvio](#startup) [iniziale,](#evaluation-phase)dalla valutazione [e](#execution-phase) dall'esecuzione delle destinazioni e delle attività che compilano il progetto. Oltre a questi input, le importazioni esterne definiscono i dettagli del processo di compilazione, [](#user-configurable-imports) incluse le importazioni [standard,](#standard-imports) ad esempio *Microsoft.Common.targets* e le importazioni configurabili dall'utente a livello di soluzione o di progetto.

## <a name="startup"></a>Avvio

MSBuild può essere richiamato da Visual Studio tramite il modello a oggetti MSBuild in *Microsoft.Build.dll* oppure richiamando l'eseguibile direttamente dalla riga di comando o in uno script, ad esempio nei sistemi ci. In entrambi i casi, gli input che influiscono sul processo di compilazione includono il file di progetto (o l'oggetto di progetto interno a Visual Studio), possibilmente un file di soluzione, variabili di ambiente e opzioni della riga di comando o gli equivalenti del modello a oggetti. Durante la fase di avvio, le opzioni della riga di comando o gli equivalenti del modello a oggetti vengono usati per configurare MSBuild, ad esempio la configurazione dei logger. Le proprietà impostate nella riga di comando usando l'opzione o vengono impostate come proprietà globali, che eseguono l'override di tutti i valori che verrebbero impostati nei file di progetto, anche se i file di progetto vengono letti in un `-property` `-p` secondo momento.

Le sezioni successive riguardano i file di input, ad esempio i file di soluzione o i file di progetto.

### <a name="solutions-and-projects"></a>Soluzioni e progetti

MSBuild istanze possono essere costituite da un progetto o da molti progetti come parte di una soluzione. Il file della soluzione non è un file XML MSBuild, ma MSBuild lo interpreta per conoscere tutti i progetti che devono essere compilati per la configurazione e le impostazioni della piattaforma fornite. Quando MSBuild elabora questo input XML, viene definito compilazione della soluzione. Include alcuni punti estendibili che consentono di eseguire qualcosa a ogni compilazione della soluzione, ma poiché questa compilazione è un'esecuzione separata dalle singole compilazioni di progetto, nessuna impostazione delle proprietà o delle definizioni di destinazione dalla compilazione della soluzione è rilevante per ogni compilazione del progetto.

Per informazioni su come estendere la compilazione della soluzione, vedere [Personalizzare la compilazione della soluzione.](customize-your-build.md#customize-the-solution-build)

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio compilazioni e MSBuild.exe compilazioni

Esistono alcune differenze significative tra quando i progetti vengono compilati in Visual Studio e quando si richiama direttamente MSBuild, tramite l'eseguibile MSBuild o quando si usa il modello a oggetti MSBuild per avviare una compilazione. Visual Studio gestisce l'ordine di compilazione del progetto per Visual Studio compilazioni; chiama solo MSBuild a livello di singolo progetto e, in caso contrario, vengono impostate due proprietà booleane ( , ) che influiscono in modo significativo sulle operazioni MSBuild `BuildingInsideVisualStudio` `BuildProjectReferences` lavoro. All'interno di ogni progetto, l'esecuzione avviene come quando viene richiamata tramite MSBuild, ma la differenza si verifica con i progetti a cui si fa riferimento. In MSBuild, quando sono necessari progetti a cui si fa riferimento, viene effettivamente eseguita una compilazione. in altre parti, esegue attività e strumenti e genera l'output. Quando una Visual Studio compilazione trova un progetto a cui si fa riferimento, MSBuild solo gli output previsti dal progetto a cui si fa riferimento; consente Visual Studio la compilazione di questi altri progetti. Visual Studio determina l'ordine di compilazione e chiama in MSBuild separatamente (in base alle esigenze), il tutto completamente sotto Visual Studio controllo dell'utente.

Un'altra differenza si verifica quando MSBuild viene richiamato con un file di soluzione, MSBuild analizza il file della soluzione, crea un file di input XML standard, lo valuta ed esegue come progetto. La compilazione della soluzione viene eseguita prima di qualsiasi progetto. Quando si compila da Visual Studio, non si verifica nulla. MSBuild il file di soluzione non viene mai visualizzato. Di conseguenza, la personalizzazione della compilazione della soluzione (usando *in precedenza. SolutionName.sln.targets e* *dopo. SolutionName.sln.targets*) si applica solo MSBuild.exe o al modello a oggetti, non Visual Studio compilazioni.

### <a name="project-sdks"></a>SDK per i progetti

La funzionalità SDK per i MSBuild di progetto è relativamente nuova. Prima di questa modifica, i file di progetto importavano in modo esplicito i file con estensione *targets* e *props* che hanno definito il processo di compilazione per un particolare tipo di progetto.

I progetti .NET Core importano la versione di .NET SDK appropriata. Vedere la panoramica, [GLI SDK del progetto .NET Core](/dotnet/core/project-sdk/overview)e il riferimento alle [proprietà](/dotnet/core/project-sdk/msbuild-props).

## <a name="evaluation-phase"></a>Fase di valutazione

Questa sezione illustra come questi file di input vengono elaborati e analizzati per produrre oggetti in memoria che determinano cosa verrà compilato.

Lo scopo della fase di valutazione è creare le strutture degli oggetti in memoria in base ai file XML di input e all'ambiente locale. La fase di valutazione è costituita da sei passaggi che elaborano i file di input, ad esempio i file XML del progetto o , e i file XML importati, denominati in genere come file con estensione *props* o *targets,* a seconda che si osezionino principalmente proprietà o definino destinazioni di compilazione. Ogni passaggio compila una parte degli oggetti in memoria usati successivamente nella fase di esecuzione per compilare i progetti, ma non vengono eseguite azioni di compilazione effettive durante la fase di valutazione. All'interno di ogni passaggio, gli elementi vengono elaborati nell'ordine in cui vengono visualizzati.

I passaggi nella fase di valutazione sono i seguenti:

- Valutare le variabili di ambiente
- Valutare le importazioni e le proprietà
- Valutare le definizioni degli elementi
- Valutare gli elementi
- Valutare [gli elementi UsingTask](usingtask-element-msbuild.md)
- Valutare le destinazioni

L'ordine di questi passaggi ha implicazioni significative ed è importante sapere quando si personalizza il file di progetto. Vedere [Ordine di valutazione delle proprietà e degli elementi](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Valutare le variabili di ambiente

In questa fase, le variabili di ambiente vengono usate per impostare proprietà equivalenti. Ad esempio, la variabile di ambiente PATH viene resa disponibile come proprietà `$(PATH)` . Quando viene eseguito dalla riga di comando o da uno script, l'ambiente dei comandi viene usato come di consueto e, quando viene eseguito da Visual Studio, viene usato l'ambiente attivo all'avvio Visual Studio comando.

### <a name="evaluate-imports-and-properties"></a>Valutare le importazioni e le proprietà

In questa fase viene letto l'intero codice XML di input, inclusi i file di progetto e l'intera catena di importazioni. MSBuild crea una struttura XML in memoria che rappresenta il codice XML del progetto e tutti i file importati. Al momento, le proprietà non presenti nelle destinazioni vengono valutate e impostate.

Come conseguenza della MSBuild tutti i file di input XML nelle prime fasi del processo, eventuali modifiche a tali input durante il processo di compilazione non influiscono sulla compilazione corrente.

Le proprietà all'esterno di qualsiasi destinazione vengono gestite in modo diverso dalle proprietà all'interno delle destinazioni. In questa fase vengono valutate solo le proprietà definite all'esterno di qualsiasi destinazione.

Poiché le proprietà vengono elaborate in ordine nel passaggio delle proprietà, una proprietà in qualsiasi punto dell'input può accedere ai valori delle proprietà visualizzati in precedenza nell'input, ma non alle proprietà visualizzate in un secondo momento.

Poiché le proprietà vengono elaborate prima della valutazione degli elementi, non è possibile accedere al valore di alcun elemento durante il passaggio delle proprietà. 

### <a name="evaluate-item-definitions"></a>Valutare le definizioni degli elementi

In questa fase vengono [interpretate le](item-definitions.md) definizioni degli elementi e viene creata una rappresentazione in memoria di queste definizioni.

### <a name="evaluate-items"></a>Valutare gli elementi

Gli elementi definiti all'interno di una destinazione vengono gestiti in modo diverso dagli elementi esterni a qualsiasi destinazione. In questa fase vengono elaborati gli elementi esterni a qualsiasi destinazione e i relativi metadati associati.  I metadati impostati dalle definizioni di elemento vengono sostituiti dall'impostazione dei metadati sugli elementi. Poiché gli elementi vengono elaborati nell'ordine in cui vengono visualizzati, è possibile fare riferimento agli elementi definiti in precedenza, ma non a quelli visualizzati in un secondo momento. Poiché gli elementi vengono passati dopo il passaggio delle proprietà, gli elementi possono accedere a qualsiasi proprietà, se definita all'esterno di qualsiasi destinazione, indipendentemente dal fatto che la definizione della proprietà venga visualizzata in un secondo momento.

### <a name="evaluate-usingtask-elements"></a>Valutare `UsingTask` gli elementi

In questa fase vengono letti [gli elementi UsingTask](usingtask-element-msbuild.md) e le attività vengono dichiarate per un uso successivo durante la fase di esecuzione.

### <a name="evaluate-targets"></a>Valutare le destinazioni

In questa fase, tutte le strutture di oggetti di destinazione vengono create in memoria, in preparazione dell'esecuzione. Non viene esere alcuna esecuzione effettiva. 

## <a name="execution-phase"></a>Fase di esecuzione

Nella fase di esecuzione, le destinazioni vengono ordinate ed eseguite e vengono eseguite tutte le attività. Ma prima di tutto, le proprietà e gli elementi definiti all'interno delle destinazioni vengono valutati insieme in una singola fase nell'ordine in cui appaiono. L'ordine di elaborazione è notevolmente diverso dal modo in cui vengono elaborate le proprietà e gli elementi non presenti in una destinazione: prima tutte le proprietà e quindi tutti gli elementi, in passaggi separati. Le modifiche alle proprietà e agli elementi all'interno di una destinazione possono essere osservate dopo la destinazione in cui sono state modificate.

### <a name="target-build-order"></a>Ordine di compilazione delle destinazioni

In un singolo progetto, le destinazioni vengono eseguite in modo seriale. Il problema centrale è come determinare l'ordine in cui compilare tutti gli elementi in modo che le dipendenze siano usate per compilare le destinazioni nell'ordine corretto.  

L'ordine di compilazione di destinazione è determinato dall'uso degli attributi `BeforeTargets` , e in ogni `DependsOnTargets` `AfterTargets` destinazione. L'ordine delle destinazioni successive può essere influenzato durante l'esecuzione di una destinazione precedente se la destinazione precedente modifica una proprietà a cui viene fatto riferimento in questi attributi.

Le regole per l'ordinamento sono descritte in [Determinare l'ordine di compilazione di destinazione.](target-build-order.md#determine-the-target-build-order) Il processo è determinato da una struttura dello stack contenente le destinazioni da compilare. La destinazione all'inizio di questa attività avvia l'esecuzione e, se dipende da qualsiasi altra operazione, tali destinazioni vengono inserite nella parte superiore dello stack e iniziano l'esecuzione.  Quando è presente una destinazione senza dipendenze, viene eseguita fino al completamento e la destinazione padre riprende.

### <a name="project-references"></a>Riferimenti al progetto

Esistono due percorsi di codice che MSBuild, quello normale, descritto qui, e l'opzione graph descritta nella sezione successiva.

I singoli progetti specificano la dipendenza da altri progetti tramite `ProjectReference` elementi. Quando un progetto nella parte superiore dello stack inizia a compilare, raggiunge il punto in cui viene eseguita la destinazione, una destinazione standard definita nei `ResolveProjectReferences` file di destinazione comuni.

`ResolveProjectReferences`richiama l'MSBuild attività con gli input degli `ProjectReference` elementi per ottenere gli output. Gli `ProjectReference` elementi vengono trasformati in elementi locali, ad esempio `Reference` . La MSBuild di esecuzione per il progetto corrente viene sospesa mentre la fase di esecuzione inizia a elaborare il progetto a cui si fa riferimento (la fase di valutazione viene eseguita per prima in base alle esigenze). Il progetto a cui si fa riferimento viene compilato solo dopo aver avviato la compilazione del progetto dipendente, quindi viene creato un albero di progetti di compilazione.

Visual Studio consente di creare dipendenze di progetto nei file di soluzione (sln). Le dipendenze vengono specificate nel file di soluzione e vengono rispettate solo quando si compila una soluzione o quando si compila all'interno di Visual Studio. Se si compila un singolo progetto, questo tipo di dipendenza viene ignorato. I riferimenti alla soluzione vengono trasformati MSBuild in elementi e successivamente `ProjectReference` vengono trattati nello stesso modo.

### <a name="graph-option"></a>Graph opzione

Se si specifica l'opzione di compilazione del grafo ( o ), diventa un concetto di prima classe `-graphBuild` `-graph` usato da `ProjectReference` MSBuild. MSBuild analizza tutti i progetti e costruisce il grafico dell'ordine di compilazione, un grafico delle dipendenze effettivo dei progetti, che viene quindi attraversato per determinare l'ordine di compilazione. Come per le destinazioni nei singoli progetti, MSBuild che i progetti a cui si fa riferimento siano compilati dopo i progetti da cui dipendono.

## <a name="parallel-execution"></a>Esecuzione parallela

Se si usa il supporto multiprocessore (o switch), MSBuild crea nodi, che MSBuild processi che usano `-maxCpuCount` `-m` i core CPU disponibili. Ogni progetto viene inviato a un nodo disponibile. All'interno di un nodo, le singole compilazioni di progetto vengono eseguite in modo seriale.

Le attività possono essere abilitate per l'esecuzione parallela impostando una variabile booleana , che viene impostata in base al valore della proprietà <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> `$(BuildInParallel)` in MSBuild. Per le attività abilitate per l'esecuzione parallela, un'utilità di pianificazione del lavoro gestisce i nodi e assegna il lavoro ai nodi.

Vedere [Compilazione di più progetti in parallelo con MSBuild](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>Importazioni standard

*Microsoft.Common.props* e *Microsoft.Common.targets* vengono entrambi importati dai file di progetto .NET (in modo esplicito o implicito nei progetti di tipo SDK) e si trovano nella *cartella MSBuild\Current\bin* in un'installazione Visual Studio. I progetti C++ hanno una propria gerarchia di importazioni; Vedere [MSBuild Internals per i progetti C++.](/cpp/build/reference/msbuild-visual-cpp-overview)

Il file *Microsoft.Common.props* imposta le impostazioni predefinite di cui è possibile eseguire l'override. Viene importato (in modo esplicito o implicito) all'inizio di un file di progetto. In questo modo, le impostazioni del progetto vengono visualizzate dopo le impostazioni predefinite, in modo da eseguirne l'override.

Il file *Microsoft.Common.targets* e i file di destinazione importati definiscono il processo di compilazione standard per i progetti .NET. Fornisce anche punti di estensione che è possibile usare per personalizzare la compilazione.

Nell'implementazione, *Microsoft.Common.targets è* un thin wrapper che importa *Microsoft.Common.CurrentVersion.targets*. Questo file contiene le impostazioni per le proprietà standard e definisce le destinazioni effettive che definiscono il processo di compilazione. La `Build` destinazione è definita qui, ma è effettivamente vuota. Tuttavia, la destinazione contiene l'attributo che specifica le singole destinazioni che costituiscono le istruzioni di compilazione effettive, ovvero `Build` `DependsOnTargets` , e `BeforeBuild` `CoreBuild` `AfterBuild` . La `Build` destinazione è definita come segue:

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

`BeforeBuild` e `AfterBuild` sono punti di estensione. Sono vuoti nel file *Microsoft.Common.CurrentVersion.targets,* ma i progetti possono fornire le proprie destinazioni e le attività che devono essere eseguite prima o dopo il `BeforeBuild` processo di compilazione `AfterBuild` principale. `AfterBuild` viene eseguito prima della destinazione no-op, , perché viene visualizzato nell'attributo nella `Build` `AfterBuild` `DependsOnTargets` `Build` destinazione, ma si verifica dopo `CoreBuild` .

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
| BuildOnlySettings | Impostazioni solo per le compilazioni reali, non per quando MSBuild viene richiamato al caricamento del progetto Visual Studio. |
| PrepareForBuild | Preparare i prerequisiti per la compilazione |
| PreBuildEvent | Punto di estensione per i progetti per definire le attività da eseguire prima della compilazione |
| ResolveProjectReferences | Analizzare le dipendenze del progetto e compilare progetti a cui si fa riferimento |
| ResolveAssemblyReferences| Individuare gli assembly a cui si fa riferimento. |
| ResolveReferences | È costituito `ResolveProjectReferences` da e per trovare tutte le `ResolveAssemblyReferences` dipendenze |
| PrepareResources | Elaborare i file di risorse |
| Resolvekeysource| Risolvere la chiave con nome sicuro usata per firmare [](../deployment/clickonce-security-and-deployment.md) l'assembly e il certificato usato per firmare ClickOnce manifesti. |
| Compilazione | Richiama il compilatore |
| ExportWindowsMDFile | Generare un file [WinMD](/uwp/winrt-cref/winmd-files) dai file WinMDModule generati dal compilatore. |
| UnmanagedUnregistration | Rimuovere/pulire le voci del Registro di sistema [interoperabilità COM](/dotnet/standard/native-interop/cominterop) da una compilazione precedente |
| GenerateSerializationAssemblies | Generare un assembly di serializzazione XML [ usandosgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe).|
| CreateSatelliteAssemblies | Creare un assembly satellite per ogni lingua univoca nelle risorse. |
| Generare manifesti | Genera [ClickOnce](../deployment/clickonce-security-and-deployment.md) manifesti di applicazione e distribuzione o un manifesto nativo. |
| GetTargetPath | Restituisce un elemento contenente il prodotto di compilazione (eseguibile o assembly) per questo progetto, con metadati. |
| PrepareForRun | Copiare gli output di compilazione nella directory finale, se sono stati modificati. |
| UnmanagedRegistration | Impostare le voci del Registro di sistema per [l'interoperabilità COM](/dotnet/standard/native-interop/cominterop) |
| IncrementalClean | Rimuovere i file prodotti in una build precedente ma che non sono stati prodotti nella build corrente. Questa operazione è necessaria per `Clean` eseguire operazioni nelle compilazioni incrementali. |
| PostBuildEvent | Punto di estensione per i progetti per definire le attività da eseguire dopo la compilazione |

Molte delle destinazioni nella tabella precedente si trovano nelle importazioni specifiche del linguaggio, ad esempio *Microsoft.CSharp.targets*. Questo file definisce i passaggi del processo di compilazione standard specifico per i progetti .NET C#. Ad esempio, contiene la destinazione `Compile` che chiama effettivamente il compilatore C#.

## <a name="user-configurable-imports"></a>Importazioni configurabili dall'utente

Oltre alle importazioni standard, è possibile aggiungere diverse importazioni per personalizzare il processo di compilazione.

- *Directory.Build.props*
- *Directory.Build.targets*

Questi file vengono letti dalle importazioni standard per tutti i progetti in qualsiasi sottocartella al loro sotto. Questo è in genere a livello di soluzione per le impostazioni per controllare tutti i progetti nella soluzione, ma potrebbe anche essere più in alto nel file system, fino alla radice dell'unità.

Il file *Directory.Build.props* viene importato da *Microsoft.Common.props,* quindi le proprietà definite in sono disponibili nel file di progetto. Possono essere ridefiniti nel file di progetto per personalizzare i valori in base al progetto. Il file *Directory.Build.targets* viene letto in dopo il file di progetto. In genere contiene destinazioni, ma in questo caso è anche possibile definire proprietà che non si desidera ridefinire per singoli progetti.

## <a name="customizations-in-a-project-file"></a>Personalizzazioni in un file di progetto

Visual Studio i file di progetto quando si apportano modifiche  **in Esplora soluzioni**, nella finestra Proprietà o in Proprietà Project , ma è anche possibile **apportare** modifiche personalizzate modificando direttamente il file di progetto.

Molti comportamenti di compilazione possono essere configurati impostando le proprietà MSBuild, nel file di progetto per le impostazioni locali di un progetto o come indicato nella sezione precedente, creando un file *Directory.Build.props* per impostare le proprietà a livello globale per intere cartelle di progetti e soluzioni. Per le compilazioni ad hoc nella riga di comando o gli script, è anche possibile usare l'opzione nella riga di comando per impostare le proprietà per una particolare chiamata `/p` di MSBuild. Per [informazioni sulle proprietà che è possibile](common-msbuild-project-properties.md) impostare, vedere Proprietà del progetto MSBuild comuni.

## <a name="next-steps"></a>Passaggi successivi

Il MSBuild ha diversi altri punti di estensione diversi da quelli descritti qui. Vedere [Personalizzare la compilazione.](customize-your-build.md) e [Come estendere il processo Visual Studio compilazione](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Vedi anche

[MSBuild](msbuild.md)
