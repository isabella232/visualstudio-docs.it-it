---
title: "Procedura: utilizzare il contesto dell'interfaccia utente basato su regole per le estensioni di Visual Studio Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710588"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Procedura: usare il contesto dell'interfaccia utente basato su regole per le estensioni di Visual StudioHow to: Use rule-based UI Context for Visual Studio extensions

Visual Studio consente il caricamento di <xref:Microsoft.VisualStudio.Shell.UIContext>VSPackage quando vengono attivati alcuni s noti. Tuttavia, questi contesti dell'interfaccia utente non sono granulari, che non lascia agli autori di estensione altra scelta, ma di scegliere un contesto dell'interfaccia utente disponibile che si attiva prima del punto che desiderano davvero il pacchetto VSPackage per caricare. Per un elenco dei contesti dell'interfaccia utente noti, vedere <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Il caricamento dei pacchetti può avere un impatto sulle prestazioni e caricarli prima del necessario non è la procedura consigliata. Visual Studio 2015 ha introdotto il concetto di contesti dell'interfaccia utente basati su regole, un meccanismo che consente agli autori di estensioni di definire le condizioni precise in cui viene attivato un contesto dell'interfaccia utente e vengono caricati i package VS associati.

## <a name="rule-based-ui-context"></a>Contesto dell'interfaccia utente basata su regoleRule-based UI Context

Una "Regola" è costituita da un nuovo contesto dell'interfaccia utente (un GUID) e da un'espressione booleana che fa riferimento a una o più operazioni "Termini" combinate con operazioni logiche "and", "or", "not". "Terms" viene valutato in modo dinamico in fase di esecuzione e l'espressione viene rivalutata ogni volta che viene modificato uno dei termini. Quando l'espressione restituisce true, viene attivato il contesto dell'interfaccia utente associato. In caso contrario, il contesto dell'interfaccia utente viene disattivato.

Il contesto dell'interfaccia utente basato su regole può essere usato in vari modi:Rule-based UI Context can be used in various ways:

1. Specificare i vincoli di visibilità per i comandi e le finestre degli strumenti. È possibile nascondere le finestre dei comandi/strumenti fino a quando non viene soddisfatta la regola di contesto dell'interfaccia utente.

2. Come vincoli di caricamento automatico: caricamento automatico dei pacchetti solo quando viene soddisfatta la regola.

3. Come attività ritardata: ritardare il caricamento fino a quando non è trascorso un intervallo specificato e la regola è ancora soddisfatta.

   Il meccanismo può essere utilizzato da qualsiasi estensione di Visual Studio.The mechanism may be used by any Visual Studio extension.

## <a name="create-a-rule-based-ui-context"></a>Creare un contesto dell'interfaccia utente basato su regoleCreate a rule-based UI Context
 Si supponga di avere un'estensione denominata TestPackage, che offre un comando di menu che si applica solo ai file con estensione *config.* Prima di VS2015, l'opzione migliore <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> era caricare TestPackage quando è stato attivato il contesto dell'interfaccia utente. Caricamento TestPackage in questo modo non è efficiente, poiché la soluzione caricata potrebbe anche non contenere un file *con estensione config.* Questi passaggi illustrano come usare il contesto dell'interfaccia utente basato su regole per attivare un contesto dell'interfaccia utente solo quando viene selezionato un file con estensione *config* e caricano TestPackage quando tale contesto dell'interfaccia utente viene attivato.

1. Definire un nuovo GUID UIContext e <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> aggiungerlo alla classe VSPackage e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Si supponga, ad esempio, che venga aggiunto un nuovo uiContext "UIContextGuid". Il GUID creato (è possibile creare un GUID facendo clic su **Strumenti** > **per creare GUID)** è "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Aggiungere quindi la seguente dichiarazione all'interno della classe del pacchetto:You then add the following declaration inside your package class:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Per gli attributi, aggiungere i seguenti valori: (Dettagli di questi attributi verranno spiegati più avanti)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Questi metadati definiscono il nuovo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e un'espressione che fa riferimento a un singolo termine, "DotConfig". Il termine "DotConfig" restituisce true ogni volta che la selezione corrente nella\\gerarchia attiva ha un nome che corrisponde al modello di espressione regolare " .config" (termina con *.config*). Il valore (Default) definisce un nome facoltativo per la regola utile per il debug.

    I valori dell'attributo vengono aggiunti a pkgdef generato in fase di compilazione.

2. Nel file VSCT per i comandi del TestPackage, aggiungere il flag "DynamicVisibility" ai comandi appropriati:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Nella sezione Visibilities di VSCT, legare i comandi appropriati al nuovo GUID UIContext definito in #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Nella sezione Simboli aggiungere la definizione di UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    A questo punto, * \** i comandi del menu di scelta rapida per i file con estensione config saranno visibili solo quando l'elemento selezionato in Esplora soluzioni è un file *con estensione config* e il pacchetto non verrà caricato fino a quando non viene selezionato uno di questi comandi.

   Successivamente, utilizzare un debugger per confermare che il pacchetto viene caricato solo quando previsto. Per eseguire il debug di TestPackage:

5. Impostare un <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> punto di interruzione nel metodo .

6. Compilare il TestPackage e avviare il debug.

7. Creare un progetto o aprirne uno.

8. Selezionare qualsiasi file con un'estensione diversa da *.config*. Il punto di interruzione non deve essere raggiunto.

9. Selezionare il file *App.Config.*

   TestPackage carica e si arresta in corrispondenza del punto di interruzione.

## <a name="add-more-rules-for-ui-context"></a>Aggiungere altre regole per il contesto dell'interfaccia utenteAdd more rules for UI Context
 Poiché le regole di contesto dell'interfaccia utente sono espressioni booleane, è possibile aggiungere altre regole limitate per un contesto dell'interfaccia utente. Ad esempio, nel contesto dell'interfaccia utente precedente, è possibile specificare che la regola si applica solo quando viene caricata una soluzione con un progetto. In questo modo, i comandi non verranno visualizzati se si apre un file *con estensione config* come file autonomo, non come parte di un progetto.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Ora l'espressione fa riferimento a tre termini. I primi due termini, "SingleProject" e "MultipleProjects", fanno riferimento ad altri contesti dell'interfaccia utente noti (da i relativi GUID). Il terzo termine, "DotConfig" è il contesto dell'interfaccia utente basato su regole definito in precedenza in questo articolo.

## <a name="delayed-activation"></a>Attivazione ritardata
 Le regole possono avere un "Ritardo" facoltativo. Il ritardo è specificato in millisecondi. Se presente, il ritardo determina il ritardo dell'attivazione o della disattivazione del contesto dell'interfaccia utente di una regola entro tale intervallo di tempo. Se la regola cambia prima dell'intervallo di ritardo, non accade nulla. Questo meccanismo può essere utilizzato per "sfalsare" i passaggi di inizializzazione, in particolare l'inizializzazione una tantera senza basarsi sui timer o per la registrazione per le notifiche di inattività.

 Ad esempio, è possibile specificare la regola di carico del test per un ritardo di 100 millisecondi:For example, you can specify your test load rule to have a delay of 100 milliseconds:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Tipi di termine

Di seguito sono riportati i vari tipi di termine supportati:

|Termine|Descrizione|
|-|-|
|nnnnnnnn-nnnn-nnnn-nnnnnnnnnnnnnnnnnn|Il GUID fa riferimento a un contesto dell'interfaccia utente. Il termine sarà true ogni volta che il contesto dell'interfaccia utente è attivo e false in caso contrario.|
|HierSingleSelectionName:\<modello>|Il termine sarà true ogni volta che la selezione nella gerarchia attiva è un singolo elemento e il nome dell'elemento selezionato corrisponde all'espressione regolare .Net specificata da "pattern".|
|UserSettingsStoreQuery:\<> di queryUserSettingsStoreQuery: query>|"query" rappresenta un percorso completo nell'archivio delle impostazioni utente, che deve restituire un valore diverso da zero. La query viene suddivisa in una raccolta e in "propertyName" nell'ultima barra.|
|ConfigSettingsStoreQuery:\<> di queryConfigSettingsStoreQuery: query>|"query" rappresenta un percorso completo nell'archivio delle impostazioni di configurazione, che deve restituire un valore diverso da zero. La query viene suddivisa in una raccolta e in "propertyName" nell'ultima barra.|
|ActiveProjectFlavor:\<> projectTypeGuid|Il termine sarà true ogni volta che il progetto attualmente selezionato viene aromatizzato (aggregato) e ha un sapore corrispondente al tipo di progetto specificato GUID.|
|ActiveEditorContentType:\<> contentType|Il termine sarà true quando il documento selezionato è un editor di testo con il tipo di contenuto specificato. Nota: quando il documento selezionato viene rinominato, questo termine non viene aggiornato fino a quando il file non viene chiuso e riaperto.|
|ActiveProjectCapability:\<espressione>|Il termine è true quando le funzionalità del progetto attivo corrispondono all'espressione fornita. Un'espressione può essere simile a VB &#124; CSharp.An expression can be something like VB &#124; CSharp.|
|SolutionHasProjectCapability:\<> dell'espressioneSolutionHasProjectCapability: Expression>|Simile a quanto sopra, ma termine è true quando la soluzione ha qualsiasi progetto caricato che corrisponde all'espressione.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Il termine sarà true ogni volta che una soluzione ha un progetto che è aromatizzato (aggregato) e ha un sapore corrispondente al tipo di progetto specificato GUID.|
|ProjectAddedItem:\<> di pattern| Il termine è true quando un file corrispondente al "modello" viene aggiunto a un progetto nel soluion che viene aperto.|
|ActiveProjectOutputType:\<outputType>|Il termine è true quando il tipo di output per il progetto attivo corrisponde esattamente.  outputType può essere un <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> numero intero o un tipo.|
|ActiveProjectBuildProperty:\<>buildProperty :\<> di espressione regolare|Il termine è true quando il progetto attivo ha la proprietà di compilazione specificata e il valore della proprietà corrisponde al filtro regex fornito. Fare riferimento a [Persistenza dei dati nei file](internals/persisting-data-in-the-msbuild-project-file.md) di progetto MSBuild per ulteriori dettagli sulle proprietà di compilazione.|
|SolutionHasProjectBuildProperty:\<>buildProperty e> di espressione regolareSolutionHasProjectBuildProperty: buildProperty>:\<regex>|Il termine è true quando la soluzione ha un progetto caricato con le corrispondenze di proprietà di compilazione e valore della proprietà specificate per il filtro regex fornito.|

## <a name="compatibility-with-cross-version-extension"></a>Compatibilità con l'estensione tra versioni

Contesti dell'interfaccia utente basata su regole è una nuova funzionalità in Visual Studio 2015 e non verrebbe portato a versioni precedenti. La non conversione a versioni precedenti crea un problema con le estensioni/pacchetti destinati a più versioni di Visual Studio.Not porting to earlier versions creates a problem with extensions/packages that target multiple versions of Visual Studio. Tali versioni devono essere caricate automaticamente in Visual Studio 2013 e versioni precedenti, ma possono trarre vantaggio dai contesti dell'interfaccia utente basati su regole per evitare il caricamento automatico in Visual Studio 2015.Those versions would have to be auto-loaded in Visual Studio 2013 and earlier, but can benefit from rule-based UI Contexts to prevent auto-loaded in Visual Studio 2015.

Per supportare tali pacchetti, le voci AutoLoadPackages nel Registro di sistema possono ora fornire un flag nel relativo campo valore per indicare che la voce deve essere ignorata in Visual Studio 2015 e versioni successive. Questo può essere fatto aggiungendo <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>un'opzione flag a . VSPackage possono ora aggiungere **skipWhenUIContextRulesActive** opzione al relativo <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attributo per indicare la voce deve essere ignorato in Visual Studio 2015 e versioni successive.
## <a name="extensible-ui-context-rules"></a>Regole di contesto dell'interfaccia utente estendibiliExtensible UI Context

In alcuni thread, i pacchetti non possono usare regole di contesto dell'interfaccia utente statiche. Si supponga, ad esempio, di disporre di un pacchetto che supporta l'estensibilità in modo che lo stato del comando sia basato su tipi di editor supportati dai provider MEF importati. Il comando è abilitato se è presente un'estensione che supporta il tipo di modifica corrente. In questi casi, il pacchetto stesso non può utilizzare una regola statica del contesto dell'interfaccia utente, poiché i termini cambierebbero a seconda delle estensioni MEF disponibili.

Per supportare tali pacchetti, i contesti dell'interfaccia utente basati su regole supportano un'espressione hardcoded "" che indica che tutti i termini sottostanti verranno uniti con OR. Ciò consente al pacchetto master di definire un contesto dell'interfaccia utente basato su regole noto e di legare lo stato del comando a questo contesto. Successivamente qualsiasi estensione MEF destinata al pacchetto master può aggiungere i termini per gli editor supportati senza influire su altri termini o sull'espressione master.

La <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentazione del costruttore mostra la sintassi per le regole di contesto dell'interfaccia utente estensibili.
