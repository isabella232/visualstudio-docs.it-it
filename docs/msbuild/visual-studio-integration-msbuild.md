---
title: Integrazione di Visual Studio (MSBuild)
titleSuffix: ''
description: Informazioni su Visual Studio possibile ospitare progetti in MSBuild, anche se sono stati creati da strumenti diversi e hanno processi di compilazione personalizzati.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 86cf3fd5eff9d183a1fdd3ebea5a29a5cd665206c9b540b584cdf5dd6a3582e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369475"
---
# <a name="visual-studio-integration-msbuild"></a>Integrazione di Visual Studio (MSBuild)

Visual Studio host MSBuild caricare e compilare progetti gestiti. Poiché MSBuild è responsabile del progetto, quasi tutti i progetti nel formato MSBuild possono essere usati correttamente in Visual Studio, anche se il progetto è stato creato da uno strumento diverso e ha un processo di compilazione personalizzato.

 Questo articolo descrive aspetti specifici dell'hosting MSBuild di Visual Studio che devono essere considerati quando si personalizzano i progetti e i file con estensione *targets* che si desidera caricare e compilare in Visual Studio. In questo modo è possibile assicurarsi che Visual Studio funzionalità come IntelliSense e il debug funzionino per il progetto personalizzato.

 Per informazioni sui progetti C++, vedere Project [file](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Estensioni dei file di progetto

 *MSBuild.exe* riconosce qualsiasi estensione di file di progetto corrispondente al modello *. \* proj*. Tuttavia, Visual Studio riconosce solo un subset di queste estensioni di file di progetto, che determinano il sistema di progetto specifico del linguaggio che carica il progetto. Visual Studio non dispone di un sistema di progetto MSBuild indipendente dalla lingua.

 Ad esempio, il sistema del progetto C# carica i file con estensione *csproj,* ma Visual Studio non è in grado di caricare un file *con estensione xxproj.* Un file di progetto per i file di origine in un linguaggio arbitrario deve usare la stessa estensione dei file di progetto Visual Basic o C# da caricare in Visual Studio.

## <a name="well-known-target-names"></a>Nomi di destinazione noti

 Facendo clic **sul comando** Compila in Visual Studio verrà eseguita la destinazione predefinita nel progetto. Spesso tale destinazione viene anche denominata `Build`. Scegliendo il comando **Ricompila** o **Pulisci** verrà effettuato un tentativo di eseguire una destinazione dello stesso nome nel progetto. Scegliendo **Pubblica** verrà eseguita una destinazione denominata `PublishOnly` nel progetto.

## <a name="configurations-and-platforms"></a>Configurazioni e piattaforme

 Le configurazioni sono rappresentate MSBuild progetti in base alle proprietà raggruppate in un `PropertyGroup` elemento che contiene un `Condition` attributo. Visual Studio queste condizioni per creare un elenco di configurazioni di progetto e piattaforme da visualizzare. Per estrarre correttamente tale elenco, le condizioni devono avere un formato simile a quello riportato di seguito:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio le condizioni per `PropertyGroup` `ItemGroup` gli elementi , , , e item a questo `Import` scopo.

## <a name="additional-build-actions"></a>Altre azioni di compilazione

 Visual Studio consente di modificare il nome del tipo di elemento di un file in un progetto con la proprietà **Azione** di compilazione della **finestra Proprietà** file. I nomi dei tipi di elemento **Compile**, **EmbeddedResource**, **Content** e **None** sono sempre elencati in questo menu, insieme a tutti gli altri nomi di tipi di elemento già presenti nel progetto. Per accertarsi che tutti i nomi dei tipi di elementi personalizzati siano sempre disponibili in questo menu, è possibile aggiungerli a un tipo di elemento denominato `AvailableItemName`. Aggiungendo, ad esempio, il codice riportato di seguito al file di progetto si aggiunge il tipo personalizzato **JScript** a questo menu per tutti i progetti che lo importano:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

Se si aggiungono nomi di tipo di elemento al tipo di elemento, gli elementi di tale tipo verranno visualizzati `AvailableItemName` in **Esplora soluzioni**.

> [!NOTE]
> Alcuni nomi di tipo di elemento sono speciali Visual Studio ma non elencati in questo elenco a discesa.

## <a name="in-process-compilers"></a>Compilatori In-Process

 Quando possibile, Visual Studio tenterà di usare la versione in-process del compilatore Visual Basic per migliorare le prestazioni. Non applicabile a C#. Per il corretto funzionamento, è necessario che vengano soddisfatte le condizioni seguenti:

- In una destinazione del progetto deve essere presente un'attività denominata `Vbc` per Visual Basic progetto.

- Il parametro `UseHostCompilerIfAvailable` dell'attività deve essere impostato su true.

## <a name="design-time-intellisense"></a>IntelliSense in fase di progettazione

 Per ottenere il supporto intelliSense Visual Studio prima che una compilazione abbia generato un assembly di output, è necessario che siano soddisfatte le condizioni seguenti:

- Deve essere presente una destinazione denominata `Compile`.

- La destinazione `Compile` o una delle relative dipendenze deve chiamare l'attività del compilatore per il progetto, ad esempio `Csc` o `Vbc`.

- Tramite la destinazione `Compile` o una delle relative dipendenze è necessario che il compilatore riceva tutti i parametri necessari per IntelliSense, in particolare tutti i riferimenti.

- Le condizioni elencate nella [sezione Compilatori in-process](#in-process-compilers) devono essere soddisfatte.

## <a name="build-solutions"></a>Creare soluzioni

 All Visual Studio, l'ordinamento del file di soluzione e della compilazione del progetto viene controllato Visual Studio stesso. Quando si compila una soluzione *conmsbuild.exe* riga di comando, MSBuild analizza il file di soluzione e ordina le compilazioni del progetto. In entrambi i casi i progetti vengono compilati singolarmente in ordine di dipendenza, senza attraversare i riferimenti progetto per progetto. Al contrario, quando i singoli progetti vengono compilati conmsbuild.exe, i riferimenti da *progetto* a progetto vengono attraversati.

 Quando si compila all'Visual Studio, la proprietà `$(BuildingInsideVisualStudio)` è impostata su `true` . Può essere usato nel progetto o nei *file con estensione targets* per fare in modo che la compilazione si comporti in modo diverso.

## <a name="display-properties-and-items"></a>Visualizzare proprietà ed elementi

 Visual Studio riconosce determinati valori e nomi di proprietà. Ad esempio, la proprietà riportata di seguito determinerà la visualizzazione di **Applicazione Windows** nella casella **Tipo di applicazione** in **Progettazione progetti**.

```xml
<OutputType>WinExe</OutputType>
```

 Il valore della proprietà può essere modificato in **Progettazione progetti** e salvato nel file di progetto. Se a una proprietà di questo tipo viene assegnato un valore non valido tramite modifica manuale, Visual Studio visualizza un avviso quando il progetto viene caricato e sostituisce il valore non valido con un valore predefinito.

 Visual Studio le impostazioni predefinite per alcune proprietà. Queste proprietà non verranno mantenute nel file di progetto a meno che non presentino valori non predefiniti.

 Le proprietà con nomi arbitrari non vengono visualizzate in Visual Studio. Per modificare proprietà arbitrarie in Visual Studio, è necessario aprire il file di progetto nell'editor XML e modificarle manualmente. Per altre informazioni, vedere la sezione [Modificare file di progetto in Visual Studio](#edit-project-files-in-visual-studio) più avanti in questo argomento.

 Gli elementi definiti nel progetto con nomi di tipo di elemento arbitrari vengono visualizzati per impostazione predefinita nella Esplora soluzioni **sotto** il nodo del progetto. Per nascondere un elemento, impostare i metadati `Visible` su `false`. Ad esempio, l'elemento seguente parteciperà al processo di compilazione, ma non verrà visualizzato **in** Esplora soluzioni .

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> I `Visible` metadati vengono ignorati da **Esplora soluzioni** per i progetti C++. Gli elementi verranno sempre visualizzati anche se `Visible` è impostato su false.

 Per impostazione predefinita, gli elementi dichiarati nei file importati nel progetto non vengono visualizzati. Gli elementi creati durante il processo di compilazione non vengono mai visualizzati in **Esplora soluzioni**.

## <a name="conditions-on-items-and-properties"></a>Condizioni per elementi e proprietà

 Durante una compilazione, tutte le condizioni sono completamente rispettate.

 Quando si determinano i valori delle proprietà da visualizzare, le proprietà che Visual Studio considera dipendenti dalla configurazione vengono valutate in modo diverso rispetto alle proprietà che considera indipendenti dalla configurazione. Per le proprietà che considera dipendente dalla configurazione, Visual Studio le proprietà e in modo appropriato e indica MSBuild di `Configuration` `Platform` valutare nuovamente il progetto. Per le proprietà considerate indipendenti dalla configurazione, la modalità di valutazione delle condizioni non è determinata.

 Le espressioni condizionali sugli elementi vengono sempre ignorate allo scopo di decidere se l'elemento deve essere visualizzato **in** Esplora soluzioni .

## <a name="debugging"></a>Debug

 Per trovare e avviare l'assembly di output e collegare il debugger, Visual Studio le proprietà `OutputPath` , e sono definite `AssemblyName` `OutputType` correttamente. Il debugger non riuscirà a connettersi se il processo di compilazione non ha causato la generazione di un file *con estensione pdb da* parte del compilatore.

## <a name="design-time-target-execution"></a>Esecuzione delle destinazioni in fase di progettazione

 Visual Studio tenta di eseguire destinazioni con determinati nomi quando carica un progetto. Tali destinazioni includono `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` e `CopyRunEnvironmentFiles`. Visual Studio queste destinazioni in modo che il compilatore possa essere inizializzato per fornire IntelliSense, il debugger possa essere inizializzato e i riferimenti visualizzati in Esplora soluzioni possono essere risolti. Se queste destinazioni non sono presenti, il progetto verrà caricato e compilato correttamente, ma l'esperienza in fase di Visual Studio non sarà completamente funzionante.

## <a name="edit-project-files-in-visual-studio"></a>Modificare file di progetto in Visual Studio

 Per modificare direttamente MSBuild progetto, è possibile aprire il file di progetto nell'editor XML Visual Studio xml.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Per scaricare e modificare un file di progetto in Visual Studio

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Scarica progetto**.

     Il progetto verrà contrassegnato come **(non disponibile)**.

2. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto non disponibile e quindi scegliere **Modifica \<Project File>**.

     Il file del progetto verrà aperto nell'editor XML di Visual Studio.

3. Modificare, salvare e chiudere il file di progetto.

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto non disponibile e scegliere **Ricarica progetto**.

## <a name="intellisense-and-validation"></a>IntelliSense e convalida

 Quando si usa l'editor XML per modificare i file di progetto, IntelliSense e la convalida sono guidati dai MSBuild di schema. Questi vengono installati nella cache dello schema, disponibile in *\<Visual Studio installation directory> \Xml\Schemas\1033\MSBuild*.

 I tipi MSBuild di base sono definiti in *Microsoft.Build.Core.xsd* e i tipi comuni usati da Visual Studio sono definiti in *Microsoft.Build.CommonTypes.xsd.* Per personalizzare gli schemi in modo da disporre di IntelliSense e della convalida per nomi di tipi di elementi personalizzati, proprietà e attività, è possibile modificare *Microsoft.Build.xsd* o creare uno schema personalizzato che includa gli schemi CommonTypes o Core. Se viene creato uno schema personalizzato, è necessario indicare all'editor XML come individuarlo tramite la finestra **Proprietà** .

## <a name="edit-loaded-project-files"></a>Modificare i file di progetto caricati

 Visual Studio memorizza nella cache il contenuto dei file di progetto e dei file importati dai file di progetto. Se si modifica un file di progetto caricato, Visual Studio verrà richiesto automaticamente di ricaricare il progetto in modo che le modifiche avranno effetto. Tuttavia, se si modifica un file importato da un progetto caricato, non verrà richiesto il ricaricamento e sarà necessario scaricare e ricaricare manualmente il progetto per rendere effettive le modifiche.

## <a name="output-groups"></a>Gruppi di output

 Diverse destinazioni definite in *Microsoft.Common.targets* hanno nomi che terminano con `OutputGroups` o `OutputGroupDependencies` . Visual Studio chiama queste destinazioni per ottenere elenchi specifici di output del progetto. Ad esempio, la destinazione `SatelliteDllsProjectOutputGroup` crea un elenco di tutti gli assembly satellite che verranno creati da una compilazione. Tali gruppi di output vengono usati da funzionalità come la pubblicazione, la distribuzione e i riferimenti progetto per progetto. I progetti che non li definiscono verranno caricati e compilati in Visual Studio, ma alcune funzionalità potrebbero non funzionare correttamente.

## <a name="reference-resolution"></a>Risoluzione dei riferimenti

 La risoluzione dei riferimenti è il processo di utilizzo degli elementi di riferimento archiviati in un file di progetto per individuare gli assembly effettivi. Visual Studio necessario attivare la risoluzione dei riferimenti per visualizzare le proprietà dettagliate per ogni riferimento nella **finestra** Proprietà. Nell'elenco riportato di seguito vengono descritti tre tipi di riferimenti e le relative modalità di risoluzione.

- Riferimenti dell'assembly:

   Il sistema di progetto chiama una destinazione con il nome noto `ResolveAssemblyReferences`. Tale destinazione deve produrre elementi con il nome di tipi di elementi `ReferencePath`. Ognuno di questi elementi deve avere una specifica dell'elemento (il valore dell'attributo `Include` di un elemento) che contiene il percorso completo del riferimento. Gli elementi devono disporre di tutti i metadati derivati dagli elementi di input passati, oltre ai nuovi metadati riportati di seguito:

  - `CopyLocal`, che indica se l'assembly deve essere copiato nella cartella di output, impostato su true o false.

  - `OriginalItemSpec`, che contiene la specifica dell'elemento originale del riferimento.

  - `ResolvedFrom`, impostato su "{TargetFrameworkDirectory}" se è stato risolto dalla directory .NET Framework.

- Riferimenti COM:

   Il sistema di progetto chiama una destinazione con il nome noto `ResolveCOMReferences`. Tale destinazione deve produrre elementi con il nome di tipi di elementi `ComReferenceWrappers`. Ognuno di questi elementi deve avere una specifica dell'elemento che contiene il percorso completo dell'assembly di interoperabilità per il riferimento COM. Gli elementi devono avere tutti i metadati derivati dagli elementi di input passati, oltre ai nuovi metadati con il nome `CopyLocal`, che indica se l'assembly deve essere copiato nella cartella di output e che può essere impostato su true o false.

- Riferimenti nativi

   Il sistema di progetto chiama una destinazione con il nome noto `ResolveNativeReferences`. Tale destinazione deve produrre elementi con il nome di tipi di elementi `NativeReferenceFile`. Gli elementi devono disporre di tutti i metadati derivati dagli elementi di input passati, oltre a un nuovo metadato singolo denominato `OriginalItemSpec`, che contiene la specifica dell'elemento originale del riferimento.

## <a name="performance-shortcuts"></a>Collegamenti alle prestazioni

 Se si usa l'IDE di Visual Studio per avviare il debug (premendo F5 o scegliendo Debug Avvia debug sulla barra dei menu) o per compilare il progetto   >   (ad esempio, Compila soluzione ), il processo di compilazione usa un controllo di aggiornamento rapido per migliorare le   >  prestazioni. In alcuni casi in cui le compilazioni personalizzate consentono di creare file che vengono a loro volta compilati, il controllo di aggiornamento rapido non identifica correttamente i file modificati. Per i progetti che necessitano di controlli di aggiornamento più approfonditi, è possibile disattivare il controllo rapido impostando la variabile di ambiente `DISABLEFASTUPTODATECHECK=1`. In alternativa, questo oggetto può essere impostato come proprietà MSBuild nel progetto o in un file importato dal progetto.

 Per le compilazioni normali in Visual Studio, il controllo di aggiornamento rapido non viene applicato e il progetto viene compilato come se la compilazione fosse richiamata a un prompt dei comandi.

## <a name="see-also"></a>Vedi anche

- [Procedura: Estendere il processo Visual Studio compilazione](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Avvio di una compilazione all'interno dell'IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrare estensioni di .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)
- [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc (attività)](../msbuild/csc-task.md)
- [Vbc (attività)](../msbuild/vbc-task.md)
