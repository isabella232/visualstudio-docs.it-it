---
title: Usare il contesto dell'interfaccia utente basato su regole per le estensioni di Visual Studio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 382a239a9fb37f079ee0ea612d68deaee17f4c12
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742983"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Procedura: usare il contesto dell'interfaccia utente basato su regole per le estensioni di Visual Studio

Visual Studio consente il caricamento di pacchetti VSPackage quando <xref:Microsoft.VisualStudio.Shell.UIContext> vengono attivati determinati oggetti noti. Questi contesti dell'interfaccia utente, tuttavia, non hanno una granularità fine, che lascia gli autori delle estensioni senza scegliere, ma per scegliere un contesto dell'interfaccia utente disponibile che viene attivato prima del punto in cui si vuole che il pacchetto VSPackage venga caricato. Per un elenco di contesti dell'interfaccia utente noti, vedere <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

Il caricamento dei pacchetti può avere un effetto sulle prestazioni e il caricamento prima del necessario non è la procedura consigliata. In Visual Studio 2015 è stato introdotto il concetto di contesti di interfaccia utente basati su regole, un meccanismo che consente agli autori di estensioni di definire le condizioni esatte in cui viene attivato un contesto dell'interfaccia utente e vengono caricati i pacchetti VSPackage associati.

## <a name="rule-based-ui-context"></a>Contesto dell'interfaccia utente basata su regole

Una "regola" è costituita da un nuovo contesto dell'interfaccia utente (GUID) e da un'espressione booleana che fa riferimento a uno o più "termini" combinati con le operazioni logiche "and", "or", "not". "Termini" vengono valutati dinamicamente in fase di esecuzione e l'espressione viene rivalutata ogni volta che viene modificato uno dei termini. Quando l'espressione restituisce true, il contesto dell'interfaccia utente associato viene attivato. In caso contrario, il contesto dell'interfaccia utente viene disattivato.

Il contesto dell'interfaccia utente basato su regole può essere usato in diversi modi:

1. Specificare i vincoli di visibilità per i comandi e le finestre degli strumenti. È possibile nascondere le finestre comandi/strumenti fino a quando non viene soddisfatta la regola del contesto dell'interfaccia utente.

2. Come vincoli di caricamento automatico: carica automaticamente i pacchetti solo quando la regola viene soddisfatta.

3. Come attività posticipata: ritardo del caricamento fino a quando non viene superato un intervallo specificato e la regola viene comunque soddisfatta.

   Il meccanismo può essere usato da qualsiasi estensione di Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Creare un contesto dell'interfaccia utente basato su regole
 Si supponga di avere un'estensione denominata TestPackage, che offre un comando di menu che si applica solo ai file con estensione *config* . Prima di VS2015, l'opzione migliore era caricare TestPackage quando il <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contesto dell'interfaccia utente è stato attivato. Il caricamento di TestPackage in questo modo non è efficiente, perché la soluzione caricata potrebbe non contenere neanche un file *config* . Questi passaggi illustrano come usare il contesto dell'interfaccia utente basato su regole per attivare un contesto dell'interfaccia utente solo quando è selezionato un file con estensione *config* e caricare TestPackage quando il contesto dell'interfaccia utente è attivato.

1. Definire un nuovo GUID UIContext e aggiungerlo alla classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Si supponga, ad esempio, che venga aggiunto un nuovo UIContext "UIContextGuid". Il GUID creato (è possibile creare un GUID facendo clic su **strumenti**  >  **Crea GUID**) è "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Si aggiunge quindi la seguente dichiarazione all'interno della classe del pacchetto:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Per gli attributi, aggiungere i valori seguenti: (i dettagli di questi attributi verranno illustrati più avanti)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Questi metadati definiscono il nuovo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e un'espressione che fa riferimento a un solo termine, "DotConfig". Il termine "DotConfig" restituisce true ogni volta che la selezione corrente nella gerarchia attiva ha un nome che corrisponde al modello di espressione regolare " \\ . config $" (termina con *. config*). Il valore (predefinito) definisce un nome facoltativo per la regola utile per il debug.

    I valori dell'attributo vengono aggiunti successivamente a pkgdef generati durante la compilazione.

2. Nel file VSCT per i comandi di TestPackage aggiungere il flag "DynamicVisibility" ai comandi appropriati:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Nella sezione visibilità di VSCT, associare i comandi appropriati al nuovo GUID UIContext definito in #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Nella sezione simboli aggiungere la definizione di UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    A questo punto, i comandi del menu di scelta rapida per i file con * \* estensione config* saranno visibili solo quando l'elemento selezionato in Esplora soluzioni è un file *. config* e il pacchetto non verrà caricato fino a quando non viene selezionato uno di questi comandi.

   Usare quindi un debugger per verificare che il pacchetto venga caricato solo quando previsto. Per eseguire il debug di TestPackage:

5. Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.

6. Compilare il TestPackage e avviare il debug.

7. Creare un progetto o aprirne uno.

8. Selezionare un file con un'estensione diversa da *. config*. Il punto di interruzione non deve essere raggiunto.

9. Selezionare il file di *App.Config* .

   TestPackage carica e si arresta in corrispondenza del punto di interruzione.

## <a name="add-more-rules-for-ui-context"></a>Aggiungere altre regole per il contesto dell'interfaccia utente
 Poiché le regole di contesto dell'interfaccia utente sono espressioni booleane, è possibile aggiungere regole più limitate per un contesto dell'interfaccia utente. Nel contesto dell'interfaccia utente precedente, ad esempio, è possibile specificare che la regola si applica solo quando viene caricata una soluzione con un progetto. In questo modo, i comandi non vengono visualizzati se si apre un file con *estensione config* come file autonomo, non come parte di un progetto.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 A questo punto l'espressione fa riferimento a tre termini. I primi due termini, "SingleProject" e "MultipleProjects", fanno riferimento ad altri contesti dell'interfaccia utente noti (in base ai relativi GUID). Il terzo termine "DotConfig" è il contesto dell'interfaccia utente basato su regole definito in precedenza in questo articolo.

## <a name="delayed-activation"></a>Attivazione ritardata
 Le regole possono avere un "ritardo" facoltativo. Il ritardo viene specificato in millisecondi. Se presente, il ritardo causa l'attivazione o la disattivazione del contesto dell'interfaccia utente di una regola da tale intervallo di tempo. Se la regola viene modificata di nuovo prima dell'intervallo di ritardo, non viene eseguita alcuna operazione. Questo meccanismo può essere usato per "sfalsare" i passaggi di inizializzazione, in particolare l'inizializzazione singola senza basarsi sui timer o la registrazione per le notifiche inattive.

 Ad esempio, è possibile specificare la regola di caricamento test per un ritardo di 100 millisecondi:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Tipi di termini

Di seguito sono riportati i diversi tipi di termini supportati:

|Termine|Descrizione|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Il GUID fa riferimento a un contesto dell'interfaccia utente. Il termine sarà true ogni volta che il contesto dell'interfaccia utente è attivo e false in caso contrario.|
|HierSingleSelectionName:\<pattern>|Il termine sarà true ogni volta che la selezione nella gerarchia attiva è un singolo elemento e il nome dell'elemento selezionato corrisponde all'espressione regolare .NET fornita da "pattern".|
|UserSettingsStoreQuery:\<query>|"query" rappresenta un percorso completo nell'archivio delle impostazioni utente, che deve restituire un valore diverso da zero. La query viene suddivisa in "Collection" e "propertyName" nell'ultima barra.|
|ConfigSettingsStoreQuery:\<query>|"query" rappresenta un percorso completo nell'archivio delle impostazioni di configurazione, che deve restituire un valore diverso da zero. La query viene suddivisa in "Collection" e "propertyName" nell'ultima barra.|
|ActiveProjectFlavor:\<projectTypeGuid>|Il termine sarà true ogni volta che il progetto attualmente selezionato viene aromatizzato (aggregato) e ha una versione corrispondente al GUID del tipo di progetto specificato.|
|ActiveEditorContentType:\<contentType>|Il termine sarà true se il documento selezionato è un editor di testo con il tipo di contenuto specificato. Nota: quando il documento selezionato viene rinominato, questo termine non viene aggiornato finché il file non viene chiuso e riaperto.|
|ActiveProjectCapability:\<Expression>|Il termine è true quando le funzionalità di progetto attive corrispondono all'espressione specificata. Un'espressione può essere simile a VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Expression>|Simile a sopra ma il termine è true quando la soluzione contiene un progetto caricato che corrisponde all'espressione.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Il termine sarà true ogni volta che una soluzione dispone di un progetto con Flavor (aggregato) e presenta una versione corrispondente al GUID del tipo di progetto specificato.|
|ProjectAddedItem:\<pattern>| Il termine è true quando un file corrispondente a "pattern" viene aggiunto a un progetto in soluion migliore che viene aperto.|
|ActiveProjectOutputType:\<outputType>|Il termine è true quando il tipo di output per il progetto attivo corrisponde esattamente.  OutputType può essere un Integer o un <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> tipo.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Il termine è true quando il progetto attivo presenta la proprietà di compilazione specificata e il valore della proprietà corrisponde al filtro Regex fornito. Per ulteriori informazioni sulle proprietà di compilazione, vedere [salvataggio permanente dei dati nei file di progetto MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) .|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Il termine è true quando la soluzione contiene un progetto caricato con la proprietà di compilazione specificata e il valore della proprietà corrisponde al filtro Regex fornito.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilità con l'estensione tra versioni

I contesti dell'interfaccia utente basati su regole sono una nuova funzionalità di Visual Studio 2015 che non verranno trasferite a versioni precedenti. Il mancato trasferimento a versioni precedenti crea un problema con estensioni/pacchetti destinati a più versioni di Visual Studio. Queste versioni dovrebbero essere caricate automaticamente in Visual Studio 2013 e versioni precedenti, ma possono trarre vantaggio dai contesti dell'interfaccia utente basati su regole per impedire che vengano caricati automaticamente in Visual Studio 2015.

Per supportare tali pacchetti, le voci AutoLoadPackages nel registro di sistema possono ora fornire un flag nel campo relativo al valore per indicare che la voce deve essere ignorata in Visual Studio 2015 e versioni successive. A tale scopo, è possibile aggiungere un'opzione flags a <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . I pacchetti VSPackage possono ora aggiungere l'opzione **SkipWhenUIContextRulesActive** al relativo <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attributo per indicare che la voce deve essere ignorata in Visual Studio 2015 e versioni successive.
## <a name="extensible-ui-context-rules"></a>Regole di contesto estendibile dell'interfaccia utente

A volte, i pacchetti non possono usare le regole di contesto dell'interfaccia utente statica. Si supponga, ad esempio, di disporre di un pacchetto che supporta l'estensibilità in modo che lo stato del comando sia basato sui tipi di editor supportati dai provider MEF importati. Il comando è abilitato se è presente un'estensione che supporta il tipo di modifica corrente. In questi casi, il pacchetto non può utilizzare una regola di contesto dell'interfaccia utente statica, poiché i termini cambiano a seconda delle estensioni MEF disponibili.

Per supportare tali pacchetti, i contesti dell'interfaccia utente basati su regole supportano un'espressione hardcoded "*" che indica che tutti i termini sottostanti verranno uniti con o. In questo modo, il pacchetto master può definire un contesto di interfaccia utente basato su regole noto e associare lo stato del comando a questo contesto. Successivamente, qualsiasi estensione MEF di destinazione per il pacchetto master può aggiungere i propri termini per gli editor che supporta senza alcun effetto su altri termini o sull'espressione master.

La documentazione del costruttore <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> Mostra la sintassi per le regole di contesto estendibile dell'interfaccia utente.
