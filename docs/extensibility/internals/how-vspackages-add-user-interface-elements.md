---
title: Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1109d6aecf2bc89f72377b282be0182c1e677ed0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311946"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente
Un pacchetto VSPackage può aggiungere elementi dell'interfaccia utente, ad esempio, i menu, barre degli strumenti e finestre degli strumenti di Visual Studio tramite il *vsct* file.

 È possibile trovare indicazioni per la progettazione di elementi dell'interfaccia utente in [linee guida sull'esperienza utente di Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>L'architettura di tabella comandi di Visual Studio
 Come accennato, l'architettura di tabella comandi supporta i suddetto principi architetturali. Come indicato di seguito sono riportati i principi alla base di astrazioni, strutture di dati e gli strumenti di architettura di tabella il comando:

- Esistono tre tipi di base degli elementi: menu, comandi e i gruppi. I menu possono essere esposte nell'interfaccia utente come i menu, sottomenu, barre degli strumenti o finestre degli strumenti. I comandi sono routine che l'utente può eseguire nell'IDE e possono essere esposte come voci di menu, pulsanti, caselle di riepilogo o altri controlli. I gruppi sono contenitori per i menu e comandi.

- Ogni elemento viene specificato da una definizione che descrive l'elemento, la priorità rispetto alle altre voci e i flag che modificano il comportamento.

- Ogni elemento ha una posizione che descrive l'elemento padre dell'elemento. Un elemento può avere più elementi padre, in modo da poter essere visualizzati in più posizioni nell'interfaccia utente.

     Tutti i comandi devono avere un gruppo come elemento padre, anche se è l'unico elemento figlio in tale gruppo. Ogni menu standard deve avere anche un gruppo padre. Le barre degli strumenti e finestre degli strumenti fungono i propri elementi padre. Un gruppo può avere come padre barra dei menu di Visual Studio principale, o qualsiasi menu di scelta, sulla barra degli strumenti o finestra degli strumenti.

### <a name="how-items-are-defined"></a>Modo in cui sono definiti gli elementi
 Oggetto *vsct* formato del file XML. Definisce gli elementi dell'interfaccia utente per un pacchetto e determina dove tali elementi vengono visualizzati nell'IDE. Ogni menu, gruppo o comando nel pacchetto viene prima assegnato un GUID e ID nel `Symbols` sezione. Nella parte restante del *vsct* file, ogni menu, comandi e gruppo viene identificato tramite la combinazione di GUID e ID. Nell'esempio seguente viene illustrato un tipico `Symbols` sezione, generata dal modello di pacchetto di Visual Studio quando un **comando di Menu** sia selezionata nel modello.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">

    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

 Elemento di primo livello del `Symbols` sezione il [elemento GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol` elementi di mapping dei nomi di GUID utilizzati per identificare i pacchetti e le relative parti componente dall'IDE.

> [!NOTE]
> I GUID vengono generati automaticamente dal modello di pacchetto di Visual Studio. È anche possibile creare un GUID univoco facendo **Crea GUID** nel **strumenti** menu.

 Il primo `GuidSymbol` elemento `guid<PackageName>Pkg`, è il GUID del pacchetto stesso. Si tratta del GUID che viene utilizzato da Visual Studio per caricare il pacchetto. In genere, non presenta elementi figlio.

 Per convenzione, i menu e comandi vengono raggruppati in un secondo `GuidSymbol` elemento `guid<PackageName>CmdSet`, e le bitmap sono in una terza `GuidSymbol` elemento `guidImages`. Non devi seguono questa convenzione, ma ogni menu, gruppo, comandi e bitmap deve essere un elemento figlio di un `GuidSymbol` elemento.

 Nella seconda `GuidSymbol` elemento, che rappresenta il set di comandi del pacchetto, sono diversi `IDSymbol` elementi. Ciascuna [elemento IDSymbol](../../extensibility/idsymbol-element.md) associa un nome a un valore numerico e può rappresentare un menu, gruppo o comando che fa parte del set di comandi. Il `IDSymbol` gli elementi nel terzo `GuidSymbol` elemento rappresentano bitmap che può essere usata come le icone per i comandi. Poiché le coppie GUID/ID devono essere univoche in un'applicazione, non due elementi figlio dello stesso `GuidSymbol` elemento può avere lo stesso valore.

### <a name="menus-groups-and-commands"></a>Menu, gruppi e i comandi
 Quando un menu, gruppo o comando è un GUID e ID, può essere aggiunto all'IDE. Ogni elemento dell'interfaccia utente debba avere gli elementi seguenti:

- Oggetto `guid` attributo che corrisponde al nome del `GuidSymbol` elemento che l'elemento dell'interfaccia utente è definito sotto.

- Un' `id` attributo che corrisponde al nome dell'oggetto associato `IDSymbol` elemento.

     Insieme, il `guid` e `id` attributi compongono le *firma* dell'elemento dell'interfaccia utente.

- Oggetto `priority` attributo che determina il posizionamento dell'elemento dell'interfaccia utente nel relativo menu padre o gruppo.

- Oggetto [elemento padre](../../extensibility/parent-element.md) dotato `guid` e `id` gli attributi che specificano la firma del menu padre o del gruppo.

#### <a name="menus"></a>Menu
 Le voci di menu viene definito come un [Menu element](../../extensibility/menu-element.md) nel `Menus` sezione. Menu di scelta deve avere `guid`, `id`, e `priority` gli attributi e un `Parent` elemento e anche i seguenti attributi aggiuntivi e gli elementi figlio:

- Oggetto `type` attributo che specifica se il menu deve essere visualizzato nell'IDE come un tipo di menu o una barra degli strumenti.

- Oggetto [elemento Strings](../../extensibility/strings-element.md) che contiene un [elemento ButtonText](../../extensibility/buttontext-element.md), che specifica il titolo del menu di scelta dell'IDE e un [elemento CommandName](../../extensibility/commandname-element.md), che consente di specificare il nome utilizzato nel **comando** finestra per accedere al menu.

- Flag opzionale. Oggetto [elemento CommandFlag](../../extensibility/command-flag-element.md) può comparire in una definizione di menu per modificare il comportamento nell'IDE o l'aspetto.

  Ogni `Menu` elemento deve avere un gruppo come elemento padre, a meno che non è un elemento, ad esempio una barra degli strumenti ancorato. Un menu ancorato è il proprio padre. Per altre informazioni sui menu e i valori per il `type` dell'attributo, vedere la [Menu element](../../extensibility/menu-element.md) documentazione.

  L'esempio seguente mostra un menu che viene visualizzato nella barra dei menu di Visual Studio, accanto al **strumenti** menu.

```xml
<Menu guid="guidTopLevelMenuCmdSet"
id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu"
          id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Gruppi
 Un gruppo è un elemento definito nel `Groups` sezione il *vsct* file. I gruppi sono soli contenitori. Non sono visualizzate nell'IDE, ad eccezione come una linea in un menu. Pertanto, un [elemento gruppo](../../extensibility/group-element.md) è definito solo per la firma, la priorità e padre.

 Un gruppo può avere un menu, un altro gruppo o se stessa come elemento padre. Tuttavia, l'elemento padre è in genere un menu o sulla barra degli strumenti. Il menu di scelta nell'esempio precedente è un figlio di `IDG_VS_MM_TOOLSADDINS` gruppo e tale gruppo è un elemento figlio della barra dei menu di Visual Studio. Il gruppo di nell'esempio seguente è un figlio del menu di scelta nell'esempio precedente.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 Perché fa parte di un menu, questo gruppo conterrà in genere i comandi. Tuttavia, potrebbe contenere anche altri menu. Si tratta di come vengono definiti i sottomenu, come illustrato nell'esempio seguente.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"
priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Comandi:
 Un comando che viene fornito per l'IDE è definito come un [Button element](../../extensibility/button-element.md) o una [elemento Combo](../../extensibility/combo-element.md). Deve essere visualizzato un menu o una barra degli strumenti, il comando deve avere un gruppo come elemento padre.

##### <a name="buttons"></a>Pulsanti
 I pulsanti sono definiti nel `Buttons` sezione. Qualsiasi voce di menu, pulsante o altro elemento che un utente fa clic per eseguire un comando singolo è considerato un pulsante. Alcuni tipi di pulsante possono includere anche la funzionalità di elenco. I pulsanti hanno corrispondono a quelle richieste e gli attributi facoltativi che contiene i menu, e può avere anche un [elemento Icon](../../extensibility/icon-element.md) che specifica il GUID e l'ID della bitmap che rappresenta il pulsante nell'IDE. Per altre informazioni sui pulsanti e i relativi attributi, vedere la [elemento Buttons](../../extensibility/buttons-element.md) documentazione.

 Il pulsante nell'esempio seguente è un figlio del gruppo di nell'esempio precedente e verrebbe visualizzata nell'IDE come una voce di menu nel menu del padre di tale gruppo.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>Casella combinata
 Casella combinata è definiti nel `Combos` sezione. Ogni `Combo` elemento rappresenta una casella di riepilogo a discesa nell'IDE. La casella di riepilogo può o potrebbe non essere accessibile in scrittura da parte degli utenti, in base al valore di `type` attributo della casella combinata. Combos contengono gli stessi elementi e il comportamento che i pulsanti hanno e può anche avere i seguenti attributi aggiuntivi:

- Oggetto `defaultWidth` attributo che specifica la larghezza in pixel.

- Un `idCommandList` attributo che specifica un elenco che contiene gli elementi che vengono visualizzati nella casella di riepilogo. L'elenco dei comandi deve essere dichiarato nello stesso `GuidSymbol` nodo che contiene la casella combinata.

  Nell'esempio seguente definisce un elemento di casella combinata.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>Bitmap
 I comandi che verranno visualizzati insieme a un'icona devono includere un `Icon` elemento che fa riferimento a una bitmap con il GUID e ID. Ogni bitmap viene definito come un [elemento Bitmap](../../extensibility/bitmap-element.md) nel `Bitmaps` sezione. L'unico obbligatorio gli attributi per un `Bitmap` definition risultano `guid` e `href`, che punta al file di origine. Se il file di origine è un elenco di risorse, un **usedList** anche l'attributo è obbligatorio, per elencare le immagini disponibili nell'elenco. Per altre informazioni, vedere la [elemento Bitmap](../../extensibility/bitmap-element.md) documentazione.

### <a name="parenting"></a>Genitorialità
 Le regole seguenti determinano come un elemento può chiamare un altro elemento del relativo sito padre.

|Elemento|Definito in questa sezione della tabella comandi|Può essere contenuto (come un elemento padre, o dalla posizione nel `CommandPlacements` sezione o entrambi)|Può contenere (definito come padre)|
|-------------| - | - | - |
|Raggruppa|[Elemento Groups](../../extensibility/groups-element.md), l'IDE, altri pacchetti VSPackage|Un menu, un gruppo, l'elemento stesso|Menu, gruppi e i comandi|
|Menu|[Elemento Menus](../../extensibility/menus-element.md), l'IDE, altri pacchetti VSPackage|1 per *n* gruppi|0 per *n* gruppi|
|ToolBar|[Elemento Menus](../../extensibility/menus-element.md), l'IDE, altri pacchetti VSPackage|L'elemento stesso|0 per *n* gruppi|
|MenuItem|[Elemento Buttons](../../extensibility/buttons-element.md), l'IDE, altri pacchetti VSPackage|1 per *n* dei gruppi, l'elemento stesso|-0 *n* gruppi|
|Button|[Elemento Buttons](../../extensibility/buttons-element.md), l'IDE, altri pacchetti VSPackage|1 per *n* dei gruppi, l'elemento stesso||
|Combo|[Elemento combos](../../extensibility/combos-element.md), l'IDE, altri pacchetti VSPackage|1 per *n* dei gruppi, l'elemento stesso||

### <a name="menu-command-and-group-placement"></a>Menu di scelta, il comando e posizionamento del gruppo
 Un menu, gruppo o comando può apparire in più di una posizione nell'IDE. Per un elemento venga visualizzato in più posizioni, è necessario aggiungerlo per il `CommandPlacements` sezione come un [elemento CommandPlacement](../../extensibility/commandplacement-element.md). Qualsiasi menu, gruppo o comando può essere aggiunto come un commandplacement. Tuttavia, le barre degli strumenti non può essere posizionate in questo modo perché non possono apparire in più posizioni sensibile al contesto.

 Avere commandplacement `guid`, `id`, e `priority` attributi. Il GUID e l'ID deve corrispondere a quelli dell'elemento che è posizionato. Il `priority` attributo determina la posizione dell'elemento in relazione gli altri elementi. Quando l'IDE unisce due o più elementi che hanno la stessa priorità, le posizioni sono definiti, poiché l'IDE non garantisce che le risorse del pacchetto vengono letti nello stesso ordine ogni volta che il pacchetto viene compilato.

 Se in più posizioni viene visualizzato un menu o un gruppo, verranno visualizzati tutti gli elementi figlio di tale menu o un gruppo in ogni istanza.

## <a name="command-visibility-and-context"></a>Contesto e la visibilità di comando
 Quando sono installati più pacchetti VSPackage, una moltitudine di menu, le voci di menu e barre degli strumenti può creare confusione nell'IDE. Per evitare questo problema, è possibile controllare la visibilità dei singoli elementi dell'interfaccia utente usando *vincoli di visibilità* e flag dei comandi.

### <a name="visibility-constraints"></a>Vincoli di visibilità
 Un vincolo di visibilità è impostato come una [elemento VisibilityItem](../../extensibility/visibilityitem-element.md) nel `VisibilityConstraints` sezione. Un vincolo di visibilità definisce i contesti dell'interfaccia utente specifici in cui è visibile l'elemento di destinazione. Un menu o un comando che è incluso in questa sezione è visibile solo quando uno dei contesti definiti è attivo. Se un menu o un comando non viene fatto riferimento in questa sezione, è sempre visibile per impostazione predefinita. In questa sezione non si applica ai gruppi.

 `VisibilityItem` gli elementi devono contenere tre attributi, come indicato di seguito: i `guid` e `id` dell'elemento dell'interfaccia utente di destinazione, e `context`. Il `context` attributo specifica quando l'elemento di destinazione sarà visibile e accetta qualsiasi contesto dell'interfaccia utente valido come relativo valore. Le costanti di contesto dell'interfaccia utente per Visual Studio sono membri del <xref:Microsoft.VisualStudio.VSConstants> classe. Ogni `VisibilityItem` elemento può accettare il valore di un solo contesto. Per applicare un secondo contesto, creare una seconda `VisibilityItem` elemento al quale punta allo stesso elemento, come illustrato nell'esempio seguente.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>Flag dei comandi
 I flag di comando seguenti possono influire sulla visibilità del menu e comandi a che si applicano.

 `AlwaysCreate` Menu viene creato anche se non contiene né gruppi di pulsanti.

 Valido per: `Menu`

 `CommandWellOnly` Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si desidera renderla disponibile per la personalizzazione di altre shell, ad esempio, associarla a una chiave. Dopo aver installato il pacchetto VSPackage, un utente può personalizzare questi comandi, aprire il **opzioni** finestra di dialogo e quindi modificando il posizionamento del comando sotto il **tastiera ambiente** categoria. Non interessa la selezione host nei menu di scelta rapida, barre degli strumenti, i controller di menu o sottomenu.

 Valida per: `Button`, `Combo`

 `DefaultDisabled` Per impostazione predefinita, il comando è disabilitato se il pacchetto VSPackage che implementa il comando non è stato caricato o non è stato chiamato il metodo QueryStatus.

 Valida per: `Button`, `Combo`

 `DefaultInvisible` Per impostazione predefinita, il comando è invisibile se il pacchetto VSPackage che implementa il comando non è stato caricato o non è stato chiamato il metodo QueryStatus.

 Deve essere combinato con il `DynamicVisibility` flag.

 Valida per: `Button`, `Combo`, `Menu`

 `DynamicVisibility` La visibilità del comando può essere modificata tramite il `QueryStatus` metodo o un GUID che viene incluso nel contesto di `VisibilityConstraints` sezione.

 Si applica ai comandi che vengono visualizzati nei menu, non sulle barre degli strumenti. Gli elementi di primo livello sulla barra degli strumenti possono essere disabilitati, ma non nascosti, quando la `OLECMDF_INVISIBLE` flag viene restituito dal `QueryStatus` (metodo).

 In un menu, questo flag indica anche che si devono essere nascosti automaticamente quando i relativi membri sono nascosti. Questo flag viene in genere assegnato al sottomenu poiché i menu di primo livello è già installato questo comportamento.

 Deve essere combinato con il `DefaultInvisible` flag.

 Valida per: `Button`, `Combo`, `Menu`

 `NoShowOnMenuController` Se un comando che include questo flag è posizionato su un controller di menu, il comando non viene visualizzato nell'elenco a discesa.

 Valido per: `Button`

 Per altre informazioni sui flag di comando, vedere la [elemento CommandFlag](../../extensibility/command-flag-element.md) documentazione.

#### <a name="general-requirements"></a>Requisiti generali
 Il comando è necessario passare la serie seguente di test prima di poter essere visualizzata e abilitato:

- Il comando è posizionato correttamente.

- Il `DefaultInvisible` flag non è impostato.

- Il menu padre oppure sulla barra degli strumenti è visibile.

- Il comando non è invisibile a causa di una voce di contesto nella [elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sezione.

- Codice di VSPackage che implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia consente di visualizzare e abilita il comando. Nessun codice interfaccia intercettato e agisce su di esso.

- Quando un utente sceglie il comando, questa diventa sottoposto alla procedura descritta in [algoritmo di Routing](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Comandi predefiniti delle chiamate
 Il [elemento UsedCommands](../../extensibility/usedcommands-element.md) consente ai package VS per accedere ai comandi forniti da altri pacchetti VSPackage o dall'IDE. A questo scopo, creare un [elemento UsedCommand](../../extensibility/usedcommand-element.md) che è il GUID e ID del comando da usare. Ciò garantisce che il comando verrà caricato da Visual Studio, anche se non fa parte della configurazione di Visual Studio corrente. Per altre informazioni, vedere [elemento UsedCommand](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Aspetto di elemento di interfaccia
 Considerazioni per la selezione e posizionamento degli elementi di comando sono i seguenti:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre molti elementi dell'interfaccia utente che vengono visualizzati in modo diverso a seconda della selezione host.

- Un elemento dell'interfaccia utente che viene definito tramite il `DefaultInvisible` flag non verrà visualizzato nell'IDE a meno che non è visualizzato uno dalla relativa implementazione di VSPackage la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodo, o associato a un determinato contesto dell'interfaccia utente nel `VisibilityConstraints` sezione.

- Anche un comando è stato posizionato potrebbe non essere visualizzato. Questo è perché l'IDE automaticamente nasconde o Visualizza alcuni comandi, a seconda delle interfacce che il pacchetto VSPackage è (o non abbia) implementato. Ad esempio, un'implementazione di VSPackage alcuni compilare interfacce voci di menu relative alla compilazione cause automaticamente da visualizzare.

- Applicando la `CommandWellOnly` flag nella definizione di elemento dell'interfaccia utente indica che il comando è possibile aggiungere solo dalla personalizzazione.

- I comandi potrebbero essere disponibili solo in determinati contesti dell'interfaccia utente, ad esempio, solo quando una finestra di dialogo viene visualizzata quando l'IDE è in visualizzazione progettazione.

- Per generare alcuni elementi dell'interfaccia utente da visualizzare nell'IDE, è necessario implementare una o più interfacce o scrivere codice.

## <a name="see-also"></a>Vedere anche
- [Estendere i menu e comandi](../../extensibility/extending-menus-and-commands.md)