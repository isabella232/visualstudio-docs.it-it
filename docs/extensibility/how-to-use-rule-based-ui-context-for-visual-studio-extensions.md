---
title: Usare il contesto dell'interfaccia utente basato su regole per Visual Studio personalizzate
titleSuffix: ''
description: Informazioni su come usare contesti dell'interfaccia utente basati su regole, che consentono agli autori di estensioni di definire le condizioni quando viene attivato un contesto dell'interfaccia utente e vengono caricati i pacchetti VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: 0ce09edd20c0c46a6b93ace77808fdfc7d5d1c5d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626250"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Procedura: Usare il contesto dell'interfaccia utente basato su regole per Visual Studio personalizzate

Visual Studio consente il caricamento di VSPackage quando vengono attivati <xref:Microsoft.VisualStudio.Shell.UIContext> alcuni pacchetti noti. Tuttavia, questi contesti dell'interfaccia utente non sono granulari in modo accurato, quindi gli autori di estensioni non hanno altra scelta che scegliere un contesto dell'interfaccia utente disponibile che si attiva prima del punto in cui volevano caricare il pacchetto VSPackage. Per un elenco di contesti dell'interfaccia utente noti, vedere <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

Il caricamento dei pacchetti può avere un impatto sulle prestazioni e caricarli prima del necessario non è la procedura consigliata. Visual Studio 2015 ha introdotto il concetto di contesti dell'interfaccia utente basati su regole, un meccanismo che consente agli autori di estensioni di definire le condizioni precise in cui viene attivato un contesto dell'interfaccia utente e vengono caricati i VSPackage associati.

## <a name="rule-based-ui-context"></a>Contesto dell'interfaccia utente basato su regole

Una "regola" è costituita da un nuovo contesto dell'interfaccia utente (GUID) e un'espressione booleana che fa riferimento a uno o più "Termini" combinati con operazioni logiche "and", "or", "not". I termini vengono valutati dinamicamente in fase di esecuzione e l'espressione viene rivalutata ogni volta che cambia uno dei termini. Quando l'espressione restituisce true, viene attivato il contesto dell'interfaccia utente associato. In caso contrario, il contesto dell'interfaccia utente viene de-attivato.

Il contesto dell'interfaccia utente basato su regole può essere usato in vari modi:

1. Specificare i vincoli di visibilità per i comandi e le finestre degli strumenti. È possibile nascondere le finestre comandi/strumenti fino a quando non viene soddisfatta la regola del contesto dell'interfaccia utente.

2. Come vincoli di caricamento automatico: caricare automaticamente i pacchetti solo quando viene soddisfatta la regola.

3. Come attività posticipata: ritardare il caricamento fino a quando non viene superato un intervallo specificato e la regola è ancora soddisfatta.

   Il meccanismo può essere usato da qualsiasi Visual Studio predefinita.

## <a name="create-a-rule-based-ui-context"></a>Creare un contesto dell'interfaccia utente basato su regole
 Si supponga di avere un'estensione denominata TestPackage, che offre un comando di menu che si applica solo ai file con *.config* predefinita. Prima di VS2015, l'opzione migliore era caricare TestPackage quando è stato attivato <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> il contesto dell'interfaccia utente. Il caricamento di TestPackage in questo modo non è efficiente, perché la soluzione caricata potrebbe non contenere neanche un file *.config* file. Questi passaggi illustrano come usare il contesto dell'interfaccia utente basato su regole per attivare un contesto dell'interfaccia utente solo quando è selezionato un file con estensione *.config* e caricare TestPackage quando tale contesto dell'interfaccia utente è attivato.

1. Definire un nuovo GUID UIContext e aggiungere alla classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Si supponga, ad esempio, che sia necessario aggiungere un nuovo UIContext "UIContextGuid". Il GUID creato (è possibile creare un GUID facendo clic su Strumenti Crea  >  **GUID)** è "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Aggiungere quindi la dichiarazione seguente all'interno della classe del pacchetto:

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

    Questi metadati definiscono il nuovo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e un'espressione che fa riferimento a un singolo termine, "DotConfig". Il termine "DotConfig" restituisce true ogni volta che la selezione corrente nella gerarchia attiva ha un nome che corrisponde al modello di espressione regolare \\ ".config$" (termina *con.config*). Il valore (Predefinito) definisce un nome facoltativo per la regola utile per il debug.

    I valori dell'attributo vengono aggiunti a pkgdef generati in fase di compilazione in un secondo momento.

2. Nel file VSCT per i comandi di TestPackage aggiungere il flag "DynamicVisibility" ai comandi appropriati:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Nella sezione Visibilità di VSCT associare i comandi appropriati al nuovo GUID UIContext definito in #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Nella sezione Simboli aggiungere la definizione di UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    A questo punto, i comandi del menu di scelta rapida per i file di.configsaranno visibili solo quando l'elemento selezionato in Esplora soluzioni è un file *.config* e il pacchetto non verrà caricato fino *\* a* quando non viene selezionato uno di questi comandi.

   Usare quindi un debugger per verificare che il pacchetto sia caricato solo quando previsto. Per eseguire il debug di TestPackage:

5. Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo .

6. Compilare TestPackage e avviare il debug.

7. Creare un progetto o aprirne uno.

8. Selezionare qualsiasi file con un'estensione diversa da *.config*. Il punto di interruzione non deve essere raggiunto.

9. Selezionare il *App.Config* file.

   TestPackage viene caricato e arrestato in corrispondenza del punto di interruzione.

## <a name="add-more-rules-for-ui-context"></a>Aggiungere altre regole per il contesto dell'interfaccia utente
 Poiché le regole del contesto dell'interfaccia utente sono espressioni booleane, è possibile aggiungere altre regole limitate per un contesto dell'interfaccia utente. Ad esempio, nel contesto dell'interfaccia utente precedente è possibile specificare che la regola si applica solo quando viene caricata una soluzione con un progetto. In questo modo, i comandi non vengono visualizzati se si apre un file *.config* come file autonomo, non come parte di un progetto.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Ora l'espressione fa riferimento a tre termini. I primi due termini, "SingleProject" e "MultipleProjects", fanno riferimento ad altri contesti dell'interfaccia utente noti (dai relativi GUID). Il terzo termine , "DotConfig" è il contesto dell'interfaccia utente basato su regole definito in precedenza in questo articolo.

## <a name="delayed-activation"></a>Attivazione ritardata
 Le regole possono avere un "Ritardo" facoltativo. Il ritardo è specificato in millisecondi. Se presente, il ritardo causa un ritardo di tale intervallo di tempo per l'attivazione o la disattivazione del contesto dell'interfaccia utente di una regola. Se la regola viene modificata prima dell'intervallo di ritardo, non accade nulla. Questo meccanismo può essere usato per "sfalsare" i passaggi di inizializzazione, in particolare l'inizializzazione una sola volta senza basarsi sui timer o registrarsi per le notifiche inattive.

 Ad esempio, è possibile specificare la regola di carico di test per un ritardo di 100 millisecondi:

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

Ecco i vari tipi di termine supportati:

|Termine|Descrizione|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Il GUID fa riferimento a un contesto dell'interfaccia utente. Il termine sarà true ogni volta che il contesto dell'interfaccia utente è attivo e false in caso contrario.|
|HierSingleSelectionName:\<pattern>|Il termine sarà true ogni volta che la selezione nella gerarchia attiva è un singolo elemento e il nome dell'elemento selezionato corrisponde all'espressione regolare .NET specificata da "pattern".|
|UserSettingsStoreQuery:\<query>|"query" rappresenta un percorso completo nell'archivio impostazioni utente, che deve restituire un valore diverso da zero. La query viene suddivisa in una "raccolta" e in "propertyName" all'ultima barra.|
|ConfigSettingsStoreQuery:\<query>|"query" rappresenta un percorso completo nell'archivio delle impostazioni di configurazione, che deve restituire un valore diverso da zero. La query viene suddivisa in una "raccolta" e in "propertyName" all'ultima barra.|
|ActiveProjectFlavor:\<projectTypeGuid>|Il termine sarà true ogni volta che il progetto attualmente selezionato viene insaccato (aggregato) e ha una versione corrispondente al GUID del tipo di progetto specificato.|
|ActiveEditorContentType:\<contentType>|Il termine sarà true quando il documento selezionato è un editor di testo con il tipo di contenuto specificato. Nota: quando il documento selezionato viene rinominato, questo termine non viene aggiornato fino a quando il file non viene chiuso e riaperto.|
|ActiveProjectCapability:\<Expression>|Il termine è true quando le funzionalità del progetto attivo corrispondono all'espressione specificata. Un'espressione può essere simile a VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Expression>|Simile al precedente, ma term è true quando la soluzione ha un progetto caricato che corrisponde all'espressione.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Il termine sarà true ogni volta che una soluzione ha un progetto insaccato (aggregato) e ha una versione corrispondente al GUID del tipo di progetto specificato.|
|ProjectAddedItem:\<pattern>| Il termine è true quando un file corrispondente al "modello" viene aggiunto a un progetto nella soluzione aperta.|
|ActiveProjectOutputType:\<outputType>|Il termine è true quando il tipo di output per il progetto attivo corrisponde esattamente.  OutputType può essere un numero intero o un <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> tipo.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Il termine è true quando nel progetto attivo è specificata la proprietà di compilazione e il valore della proprietà corrisponde al filtro regex specificato. Per altri [dettagli sulle proprietà di compilazione, vedere Persisting Data in MSBuild Project Files](internals/persisting-data-in-the-msbuild-project-file.md) (Persistenza dei dati nei file di compilazione).|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Il termine è true quando la soluzione ha un progetto caricato con la proprietà di compilazione e il valore della proprietà specificati corrispondono al filtro regex fornito.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilità con l'estensione tra versioni

I contesti dell'interfaccia utente basati su regole sono una nuova funzionalità di Visual Studio 2015 e non verrebbero convertire in versioni precedenti. Il non porting a versioni precedenti crea un problema con estensioni/pacchetti che hanno come destinazione più versioni Visual Studio. Queste versioni devono essere caricate automaticamente in Visual Studio 2013 e versioni precedenti, ma possono trarre vantaggio dai contesti dell'interfaccia utente basati su regole per impedire il caricamento automatico in Visual Studio 2015.

Per supportare tali pacchetti, le voci AutoLoadPackages nel Registro di sistema possono ora fornire un flag nel campo del valore per indicare che la voce deve essere ignorata in Visual Studio 2015 e successive. Questa operazione può essere eseguita aggiungendo un'opzione flags a <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . I pacchetti VSPackage possono ora aggiungere **l'opzione SkipWhenUIContextRulesActive** al relativo attributo per indicare che la voce deve essere ignorata in Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 2015 e successive.
## <a name="extensible-ui-context-rules"></a>Regole del contesto dell'interfaccia utente estendibile

In alcuni casi, i pacchetti non possono usare regole di contesto dell'interfaccia utente statiche. Si supponga, ad esempio, di avere un pacchetto che supporta l'estendibilità in modo che lo stato del comando sia basato sui tipi di editor supportati dai provider MEF importati. Il comando è abilitato se è presente un'estensione che supporta il tipo di modifica corrente. In questi casi, il pacchetto stesso non può usare una regola di contesto dell'interfaccia utente statica, poiché i termini cambiano a seconda delle estensioni MEF disponibili.

Per supportare tali pacchetti, i contesti dell'interfaccia utente basati su regole supportano un'espressione hardcoded "*" che indica che tutti i termini sottostanti verranno uniti con OR. In questo modo il pacchetto master può definire un contesto dell'interfaccia utente basato su regole noto e associarne lo stato del comando a questo contesto. Successivamente, qualsiasi estensione MEF destinata al pacchetto master può aggiungere i termini per gli editor supportati senza influire su altri termini o sull'espressione master.

La documentazione del costruttore <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> illustra la sintassi per le regole del contesto dell'interfaccia utente estendibile.
