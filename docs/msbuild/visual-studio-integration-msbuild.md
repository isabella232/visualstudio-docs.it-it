---
title: Integrazione di Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631198"
---
# <a name="visual-studio-integration-msbuild"></a>Integrazione di Visual Studio (MSBuild)

Visual Studio ospita MSBuild per caricare e compilare progetti gestiti. Poiché MSBuild è responsabile del progetto, quasi tutti i progetti nel formato MSBuild possono essere utilizzati correttamente in Visual Studio, anche se il progetto è stato creato da uno strumento diverso e dispone di un processo di compilazione personalizzato.

 In questo articolo vengono descritti aspetti specifici dell'hosting MSBuild di Visual Studio che devono essere considerati quando si personalizzano i progetti e i file *con estensione targets* che si desidera caricare e compilare in Visual Studio. In questo modo sarà possibile assicurarsi che le funzionalità di Visual Studio come IntelliSense e il debug funzionino per il progetto personalizzato.

 Per informazioni sui progetti in C, consultate File di [progetto.](/cpp/build/reference/project-files)

## <a name="project-file-name-extensions"></a>Estensioni dei file di progetto

 *MSBuild.exe* riconosce qualsiasi estensione di file di progetto corrispondente al modello *.\* proj*. Tuttavia, Visual Studio riconosce solo un sottoinsieme di queste estensioni di file di progetto, che determinano il sistema di progetto specifico del linguaggio che caricherà il progetto. Visual Studio non dispone di un sistema di progetto basato su MSBuild indipendente dal linguaggio.

 Ad esempio, il sistema del progetto C'è carica i file *con estensione csproj,* ma Visual Studio non è in grado di caricare un file *con estensione xxproj.* Un file di progetto per i file di origine in un linguaggio arbitrario deve utilizzare la stessa estensione dei file di progetto di Visual Basic o di C, da caricare in Visual Studio.

## <a name="well-known-target-names"></a>Nomi di destinazione noti

 Facendo clic sul comando **Compila** in Visual Studio verrà eseguita la destinazione predefinita nel progetto. Spesso tale destinazione viene anche denominata `Build`. Scegliendo il comando **Ricompila** o **Pulisci** verrà effettuato un tentativo di eseguire una destinazione dello stesso nome nel progetto. Scegliendo **Pubblica** verrà eseguita una destinazione denominata `PublishOnly` nel progetto.

## <a name="configurations-and-platforms"></a>Configurazioni e piattaforme

 Le configurazioni sono rappresentate nei progetti `PropertyGroup` MSBuild `Condition` per proprietà raggruppate in un elemento che contiene un attributo. Visual Studio esamina queste condizioni per creare un elenco di configurazioni di progetto e piattaforme da visualizzare. Per estrarre correttamente tale elenco, le condizioni devono avere un formato simile a quello riportato di seguito:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 In Visual Studio vengono `PropertyGroup` `ItemGroup`esaminate le condizioni sugli elementi , , `Import`, , e gli elementi dell'elemento per questo scopo.

## <a name="additional-build-actions"></a>Altre azioni di compilazione

 Visual Studio consente di modificare il nome del tipo di elemento di un file in un progetto con la proprietà Operazione di **compilazione** della finestra **Proprietà file.** I nomi dei tipi di elemento **Compile**, **EmbeddedResource**, **Content** e **None** sono sempre elencati in questo menu, insieme a tutti gli altri nomi di tipi di elemento già presenti nel progetto. Per accertarsi che tutti i nomi dei tipi di elementi personalizzati siano sempre disponibili in questo menu, è possibile aggiungerli a un tipo di elemento denominato `AvailableItemName`. Aggiungendo, ad esempio, il codice riportato di seguito al file di progetto si aggiunge il tipo personalizzato **JScript** a questo menu per tutti i progetti che lo importano:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Alcuni nomi di tipo di elemento sono speciali per Visual Studio, ma non elencati in questo elenco a discesa.

## <a name="in-process-compilers"></a>Compilatori In-Process

 Quando possibile, Visual Studio tenterà di utilizzare la versione in-process del compilatore Visual Basic per migliorare le prestazioni. (Non è applicabile a C.) Affinché questo funzioni correttamente, devono essere soddisfatte le seguenti condizioni:

- In una destinazione del progetto, deve `Vbc` essere presente un'attività denominata per i progetti Visual Basic.

- Il parametro `UseHostCompilerIfAvailable` dell'attività deve essere impostato su true.

## <a name="design-time-intellisense"></a>IntelliSense in fase di progettazione

 Per ottenere il supporto IntelliSense in Visual Studio prima che una compilazione abbia generato un assembly di output, devono essere soddisfatte le condizioni seguenti:To get IntelliSense support in Visual Studio before a build has generated an output assembly, the following conditions must be met:

- Deve essere presente una destinazione denominata `Compile`.

- La destinazione `Compile` o una delle relative dipendenze deve chiamare l'attività del compilatore per il progetto, ad esempio `Csc` o `Vbc`.

- Tramite la destinazione `Compile` o una delle relative dipendenze è necessario che il compilatore riceva tutti i parametri necessari per IntelliSense, in particolare tutti i riferimenti.

- Le condizioni elencate nella sezione [Compilatori in-process](#in-process-compilers) devono essere soddisfatte.

## <a name="build-solutions"></a>Creare soluzioni

 All'interno di Visual Studio, il file di soluzione e l'ordine di compilazione del progetto sono controllati da Visual Studio stesso. Quando si compila una soluzione con *msbuild.exe* nella riga di comando, MSBuild analizza il file di soluzione e ordina le compilazioni del progetto. In entrambi i casi i progetti vengono compilati singolarmente in ordine di dipendenza, senza attraversare i riferimenti progetto per progetto. Al contrario, quando i singoli progetti vengono compilati con *msbuild.exe*, i riferimenti da progetto a progetto vengono attraversati.

 Durante la compilazione all'interno di Visual Studio, la proprietà `$(BuildingInsideVisualStudio)` è impostata su `true`. Può essere utilizzato nel progetto o nei file *con estensione targets* per fare in modo che la compilazione si comporti in modo diverso.

## <a name="display-properties-and-items"></a>Visualizzare proprietà ed elementi

 Visual Studio riconosce determinati nomi e valori di proprietà. Ad esempio, la proprietà riportata di seguito determinerà la visualizzazione di **Applicazione Windows** nella casella **Tipo di applicazione** in **Progettazione progetti**.

```xml
<OutputType>WinExe</OutputType>
```

 Il valore della proprietà può essere modificato in **Progettazione progetti** e salvato nel file di progetto. Se a tale proprietà viene assegnato un valore non valido mediante modifica manuale, Visual Studio visualizza un avviso quando il progetto viene caricato e sostituisce il valore non valido con un valore predefinito.

 Visual Studio riconosce le impostazioni predefinite per alcune proprietà. Queste proprietà non verranno mantenute nel file di progetto a meno che non presentino valori non predefiniti.

 Le proprietà con nomi arbitrari non vengono visualizzate in Visual Studio.Properties with arbitrary names are not displayed in Visual Studio. Per modificare proprietà arbitrarie in Visual Studio, è necessario aprire il file di progetto nell'editor XML e modificarle manualmente. Per altre informazioni, vedere la sezione [Modificare file di progetto in Visual Studio](#edit-project-files-in-visual-studio) più avanti in questo argomento.

 Gli elementi definiti nel progetto con nomi di tipo di elemento arbitrari vengono visualizzati per impostazione predefinita in **Esplora soluzioni** nel nodo del progetto. Per nascondere un elemento, impostare i metadati `Visible` su `false`. Ad esempio, l'elemento seguente parteciperà al processo di compilazione ma non verrà visualizzato in **Esplora soluzioni**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> I `Visible` metadati vengono ignorati da **Esplora soluzioni** per i progetti in C. Gli elementi verranno `Visible` sempre visualizzati anche se è impostato su false.

 Per impostazione predefinita, gli elementi dichiarati nei file importati nel progetto non vengono visualizzati. Gli elementi creati durante il processo di compilazione non vengono mai visualizzati in **Esplora soluzioni**.

## <a name="conditions-on-items-and-properties"></a>Condizioni per elementi e proprietà

 Durante una compilazione, tutte le condizioni sono completamente rispettate.

 Quando si determinano i valori delle proprietà da visualizzare, le proprietà che Visual Studio considera dipendenti dalla configurazione vengono valutate in modo diverso rispetto alle proprietà considerate indipendenti dalla configurazione. Per le proprietà considerate dipendenti dalla `Configuration` configurazione, Visual Studio imposta le proprietà e `Platform` in modo appropriato e indica a MSBuild di rivalutare il progetto. Per le proprietà considerate indipendenti dalla configurazione, la modalità di valutazione delle condizioni non è determinata.

 Le espressioni condizionali sugli elementi vengono sempre ignorate ai fini della decisione se l'elemento deve essere visualizzato in **Esplora soluzioni**.

## <a name="debugging"></a>Debug

 Per trovare e avviare l'assembly di output e `OutputPath`connettere il debugger, Visual Studio necessita delle proprietà , `AssemblyName`e `OutputType` definito correttamente. Il debugger non riuscirà a connettersi se il processo di compilazione non ha causato la generazione di un file *PDB* da parte del compilatore.

## <a name="design-time-target-execution"></a>Esecuzione delle destinazioni in fase di progettazione

 Visual Studio tenta di eseguire destinazioni con determinati nomi quando carica un progetto. Tali destinazioni includono `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` e `CopyRunEnvironmentFiles`. Visual Studio esegue queste destinazioni in modo che il compilatore possa essere inizializzato per fornire IntelliSense, il debugger può essere inizializzato e i riferimenti visualizzati in Esplora soluzioni possono essere risolti. Se queste destinazioni non sono presenti, il progetto verrà caricato e compilato correttamente, ma l'esperienza in fase di progettazione in Visual Studio non sarà completamente funzionale.

## <a name="edit-project-files-in-visual-studio"></a>Modificare file di progetto in Visual Studio

 Per modificare direttamente un progetto MSBuild, è possibile aprire il file di progetto nell'editor XML di Visual Studio.To edit an MSBuild project directly, you can open the project file in the Visual Studio XML editor.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Per scaricare e modificare un file di progetto in Visual Studio

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto e scegliere **Scarica progetto**.

     Il progetto verrà contrassegnato come **(non disponibile)**.

2. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto non disponibile e scegliere **Modifica \<File progetto>**.

     Il file del progetto verrà aperto nell'editor XML di Visual Studio.

3. Modificare, salvare e chiudere il file di progetto.

4. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto non disponibile e scegliere **Ricarica progetto**.

## <a name="intellisense-and-validation"></a>IntelliSense e convalida

 Quando si utilizza l'editor XML per modificare i file di progetto, IntelliSense e la convalida sono guidati dai file di schema MSBuild. Questi vengono installati nella cache dello schema, che si trova nella * \<directory*di installazione di Visual Studio> .

 I tipi MSBuild principali sono definiti in *Microsoft.Build.Core.xsd* e i tipi comuni utilizzati da Visual Studio sono definiti in *Microsoft.Build.CommonTypes.xsd*. Per personalizzare gli schemi in modo da disporre di IntelliSense e della convalida per i nomi, le proprietà e le attività dei tipi di elemento personalizzati, è possibile modificare *Microsoft.Build.xsd*oppure creare uno schema personalizzato che includa gli schemi CommonTypes o Core. Se viene creato uno schema personalizzato, è necessario indicare all'editor XML come individuarlo tramite la finestra **Proprietà** .

## <a name="edit-loaded-project-files"></a>Modificare i file di progetto caricati

 Visual Studio memorizza nella cache il contenuto dei file di progetto e dei file importati dai file di progetto. Se si modifica un file di progetto caricato, Visual Studio richiederà automaticamente di ricaricare il progetto in modo che le modifiche abbiano effetto. Tuttavia, se si modifica un file importato da un progetto caricato, non verrà richiesto il ricaricamento e sarà necessario scaricare e ricaricare manualmente il progetto per rendere effettive le modifiche.

## <a name="output-groups"></a>Gruppi di output

 Diverse destinazioni definite in *Microsoft.Common.targets* hanno nomi che terminano in `OutputGroups` o `OutputGroupDependencies`. Visual Studio chiama queste destinazioni per ottenere elenchi specifici di output di progetto. Ad esempio, la destinazione `SatelliteDllsProjectOutputGroup` crea un elenco di tutti gli assembly satellite che verranno creati da una compilazione. Tali gruppi di output vengono usati da funzionalità come la pubblicazione, la distribuzione e i riferimenti progetto per progetto. I progetti che non li definiscono verranno caricati e compilati in Visual Studio, ma alcune funzionalità potrebbero non funzionare correttamente.

## <a name="reference-resolution"></a>Risoluzione dei riferimenti

 La risoluzione dei riferimenti è il processo di utilizzo degli elementi di riferimento archiviati in un file di progetto per individuare gli assembly effettivi. Visual Studio deve attivare la risoluzione dei riferimenti per visualizzare le proprietà dettagliate per ogni riferimento nel **proprietà** finestra. Nell'elenco riportato di seguito vengono descritti tre tipi di riferimenti e le relative modalità di risoluzione.

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

 Se si utilizza l'IDE di Visual Studio per avviare il debug (scegliendo il tasto F5 o scegliendo **Debug** > di**avvio** debug nella barra dei menu) o per compilare il progetto (ad esempio, **Compila** > **soluzione**di compilazione ), il processo di compilazione utilizza un controllo di aggiornamento rapido per migliorare le prestazioni. In alcuni casi in cui le compilazioni personalizzate consentono di creare file che vengono a loro volta compilati, il controllo di aggiornamento rapido non identifica correttamente i file modificati. Per i progetti che necessitano di controlli di aggiornamento più approfonditi, è possibile disattivare il controllo rapido impostando la variabile di ambiente `DISABLEFASTUPTODATECHECK=1`. In alternativa, questo oggetto può essere impostato come proprietà MSBuild nel progetto o in un file importato dal progetto.

 Per le compilazioni normali in Visual Studio, il controllo di aggiornamento rapido non viene applicato e il progetto viene compilato come se la compilazione fosse richiamata a un prompt dei comandi.

## <a name="see-also"></a>Vedere anche

- [Procedura: estendere il processo di compilazione di Visual StudioHow to: Extend the Visual Studio build process](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Avvio di una compilazione all'interno dell'IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrare estensioni di .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)
- [Elemento di destinazione (MSBuild)](../msbuild/target-element-msbuild.md)
- [Attività Csc](../msbuild/csc-task.md)
- [Attività Vbc](../msbuild/vbc-task.md)
