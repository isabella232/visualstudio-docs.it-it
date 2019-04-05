---
title: "Procedura: Usare il contesto dell'interfaccia utente basata su regole per le estensioni | Microsoft Docs"
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: fdaa8396049da2a0d875282b13eb2744bedbdd29
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955344"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Procedura: Usare un contesto di interfaccia utente basato su regole per le estensioni di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio consente il caricamento di VSPackage durante determinati noto <xref:Microsoft.VisualStudio.Shell.UIContext>s vengono attivati. Tuttavia, questi contesti dell'interfaccia utente non sono molto accurati più capillare, non lasciando gli autori delle estensioni nessuna scelta ma per il prelievo di un contesto dell'interfaccia utente disponibili che viene attivato prima del punto di lo desiderano VSPackage da caricare. Per un elenco di contesti dell'interfaccia utente ben noti, vedere <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

 Caricamento dei pacchetti può avere un impatto sulle prestazioni e caricarli prima di quanto sono necessarie, non è la procedura consigliata. Visual Studio 2015 ha introdotto il concetto dei contesti di interfaccia utente basata su regole, un meccanismo che consente agli autori di estensioni definire le condizioni precise in cui viene attivato un contesto dell'interfaccia utente e associati i pacchetti VSPackage caricato.

## <a name="rule-based-ui-context"></a>Contesto dell'interfaccia utente basata su regole
 Una "regola" è costituito da un nuovo contesto dell'interfaccia utente (un GUID) e un'espressione booleana che fa riferimento a uno o più "condizioni" combinata con logica "and", "or", "non" operazioni. "Condizioni" vengono valutate dinamicamente in fase di esecuzione e l'espressione verrà nuovamente valutata ogni volta che una delle modifiche apportate al relativo termini. Quando l'espressione restituisce true, viene attivato il contesto dell'interfaccia utente associato. In caso contrario, il contesto dell'interfaccia utente è disattivato.

 Contesto dell'interfaccia utente basata su regole può essere usato in diversi modi:

1. Specificare i vincoli di visibilità per comandi e finestre degli strumenti. È possibile nascondere le finestre degli strumenti di comandi/fino a quando non viene soddisfatta la regola di contesto dell'interfaccia utente.

2. Caricare i vincoli come auto: caricamento automatico dei pacchetti solo quando viene soddisfatta la regola

3. Posticipata di attività: ritardare il caricamento fino a quando non è trascorso un intervallo specificato e ancora viene soddisfatta la regola.

   Il meccanismo può essere usato da qualsiasi estensione di Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Creare un contesto dell'interfaccia utente basata su regole
 Si supponga di avere un'estensione denominata TestPackage, che offre un comando di menu che viene applicato solo ai file con estensione "config". Prima di Visual Studio 2015, l'opzione migliore è stato caricare TestPackage quando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contesto dell'interfaccia utente è stato attivato. Ciò non è efficiente, poiché la soluzione caricata non può contenere anche un file con estensione config. Invia i tuoi commenti vedere come contesto dell'interfaccia utente basata su regole può essere usato per attivare un contesto dell'interfaccia utente solo quando un file con estensione config sia selezionata e caricare TestPackage quando viene attivato quel contesto dell'interfaccia utente.

1. Definire un nuovo GUID UIContext e aggiungere alla classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Ad esempio, si supponga che un nuovo UIContext "UIContextGuid" deve essere aggiunto. GUID creato (è possibile creare un GUID facendo clic su Strumenti -> creare un guid) è "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Quindi aggiungere il codice seguente all'interno della classe del pacchetto:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Per gli attributi, aggiungere quanto segue: (Dettagli di questi attributi verranno spiegati più avanti)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Questi metadati definiscono il nuovo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e un'espressione che fa riferimento a un singolo termine, "DotConfig". Il termine "DotConfig" restituisce true ogni volta che la selezione corrente nella gerarchia attiva ha un nome che corrisponde al criterio di espressione regolare "\\config$" (termina con "config"). Il valore (Default) definisce un nome facoltativo per la regola utile per il debug.

    I valori dell'attributo vengono aggiunti a pkgdef generati durante la fase di compilazione in un secondo momento.

2. Nel file VSCT per i comandi del TestPackage, aggiungere il flag "DynamicVisibility" per i comandi appropriati:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Nella sezione visibilità di VSCT, associare i comandi appropriati per il nuovo UIContext GUID definito in #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>
   </VisibilityConstraints>
   ```

4. Nella sezione Symbols, aggiungere la definizione del UIContext:

   ```xml
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    A questo punto, i comandi di menu di scelta rapida per i file *. config sarà visibili solo quando l'elemento selezionato in Esplora soluzioni è un file "config" e il pacchetto non verrà caricato finché non viene selezionato uno di tali comandi.

   Successivamente, utilizziamo un debugger per verificare che il pacchetto viene caricato solo quando è previsto. Per eseguire il debug TestPackage:

5. Impostare un punto di interruzione il <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (metodo).

6. Compilare il TestPackage e avviare il debug.

7. Creare un progetto o aprire uno.

8. Selezionare tutti i file con estensione diversa da. config. Non verrà raggiunto il punto di interruzione.

9. Selezionare il file app. config.

   Il TestPackage carica e si arresta in corrispondenza del punto di interruzione.

## <a name="adding-more-rules-for-ui-context"></a>Aggiunta di altre regole per il contesto dell'interfaccia utente
 Poiché le regole di contesto dell'interfaccia utente sono espressioni booleane, è possibile aggiungere regole con maggiori restrizioni per un contesto dell'interfaccia utente. Ad esempio, nel contesto dell'interfaccia utente sopra riportato, è possibile specificare che la regola viene applicata solo quando viene caricata una soluzione con un progetto. In questo modo, i comandi non vengono visualizzati se si apre un file "config" come file autonomo e non come parte di un progetto.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 A questo punto l'espressione fa riferimento a tre condizioni. I primi due termini, "SingleProject" e "MultipleProjects", fare riferimento ad altri contesti dell'interfaccia utente ben noto (in base al GUID). Il termine terzo, "DotConfig" è il contesto dell'interfaccia utente basata su regole definite in precedenza.

## <a name="delayed-activation"></a>Attivazione ritardata
 Le regole possono avere un "ritardo" facoltativo. Il ritardo specificato in millisecondi. Se presente, il ritardo causa l'attivazione o la disattivazione del contesto dell'interfaccia utente della regola per essere posticipato da tale intervallo di tempo. Se le modifiche alle regole esegue il backup prima dell'intervallo di ritardo, quindi non accade nulla. Questo meccanismo può essere utilizzato "sfalsare" passaggi di inizializzazione, in particolare l'inizializzazione unica senza basarsi su timer o alla registrazione per le notifiche di inattività.

 Ad esempio, è possibile specificare la regola di test di carico per hanno un ritardo di 100 millisecondi:

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
 Ecco i vari tipi di termini che sono supportati:

|||
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Il GUID si riferisce a un contesto dell'interfaccia utente. Al termine sarà true ogni volta che il contesto dell'interfaccia utente è attivo e false in caso contrario.|
|HierSingleSelectionName:\<pattern>|Al termine sarà true ogni volta che la selezione nella gerarchia attiva è un singolo elemento e il nome dell'elemento selezionato corrisponde all'espressione regolare .net specificato da "pattern".|
|UserSettingsStoreQuery:\<query>|"query" rappresenta un percorso completo nell'archivio delle impostazioni utente che deve restituire un valore diverso da zero. La query viene suddivisa in un "collection" e "propertyName" nell'ultima barra.|
|ConfigSettingsStoreQuery:\<query>|"query" rappresenta un percorso completo nell'archivio delle impostazioni di configurazione che deve restituire un valore diverso da zero. La query viene suddivisa in un "collection" e "propertyName" nell'ultima barra.|
|ActiveProjectFlavor:\<projectTypeGuid>|Al termine verrà attivato ogni volta che il progetto attualmente selezionato è flavored (valore aggregato) e dispone di una versione che corrisponde al tipo di progetto specificato GUID.|
|ActiveEditorContentType:\<contentType>|Al termine sarà true quando il documento selezionato è un editor di testo con il tipo di contenuto specificato.|
|ActiveProjectCapability:\<espressione >|Il termine è true quando le funzionalità del progetto attivo corrisponde all'espressione specificata. Un'espressione può essere simile a VB &#124; CSharp|
|SolutionHasProjectCapability:\<Expression>|Analogamente al precedente ma termine è true quando si dispone di qualsiasi progetto caricato corrispondente all'espressione.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Al termine sarà true ogni volta che una soluzione di progetto che è flavored (valore aggregato) che ha una versione che corrisponde al tipo di progetto specificato GUID.|



## <a name="compatibility-with-cross-version-extension"></a>Compatibilità con l'estensione tra versioni
 Regola in base i contesti dell'interfaccia utente è una nuova funzionalità di Visual Studio 2015 e potrebbe non essere trasferito a versioni precedenti. Questo costituisce un problema con le estensioni/pacchetti destinati a più versioni di Visual Studio che dovrà essere caricato automaticamente in Visual Studio 2013 e versioni precedenti, ma possono trarre vantaggio dal basato su regole contesti dell'interfaccia utente per evitare che viene caricato automaticamente in Visual Studio 2015.

 Per supportare tali pacchetti, AutoLoadPackages voci nel Registro di sistema possono ora specificare un flag nel relativo campo valore per indicare che la voce deve essere ignorata in Visual Studio 2015 e versioni successive. Questa operazione può essere eseguita mediante l'aggiunta di un'opzione di flag per <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Ora è possono aggiungere i pacchetti VSPackage **SkipWhenUIContextRulesActive** possibilità loro <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attributo per indicare la voce deve essere ignorata in Visual Studio 2015 e versioni successive.

## <a name="extensible-ui-context-rules"></a>Regole di contesto dell'interfaccia utente estendibile
 In alcuni casi, i pacchetti non è possibile usare regole statiche di contesto dell'interfaccia utente. Ad esempio, si supponga di che avere un pacchetto che supportano l'estendibilità in modo che lo stato del comando si basa sui tipi di editor che sono supportati dai provider di MEF importati. Il comando è abilitato se c'è un'estensione che supportano il tipo di modifica corrente. In questi casi il pacchetto stesso non è possibile usare una regola di contesto dell'interfaccia utente statica, poiché le condizioni cambierebbero a seconda di quale MEF sono disponibili estensioni.

 Per supportare tali pacchetti, i contesti dell'interfaccia utente basato su regole supportano un'espressione hardcoded "*" che indica tutte le condizioni che seguono viene poi unito o. In questo modo per il pacchetto master definire una regola nota basati su contesto dell'interfaccia utente e collegare il relativo stato di comandi a questo contesto. In un secondo momento qualsiasi estensione MEF per il pacchetto master di destinazione possa aggiungere relative condizioni per gli editor che supporta senza alcun impatto sugli altri termini o l'espressione master.

 Il costruttore <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentazione viene illustrata la sintassi per le regole di contesto dell'interfaccia utente estendibili.
