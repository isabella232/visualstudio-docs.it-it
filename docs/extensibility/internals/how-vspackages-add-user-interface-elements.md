---
title: Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente | Microsoft Docs
description: Informazioni su come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente, ad esempio menu, barre degli strumenti e finestre degli strumenti, a Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3e2fe51c365e3e6936a73aef9d4de9d52024d47
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761088"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente
Un pacchetto VSPackage può aggiungere elementi dell'interfaccia utente (UI), ad esempio menu, barre degli strumenti e finestre degli strumenti, a Visual Studio tramite il file con *estensione vsct* .

È possibile trovare linee guida di progettazione per gli elementi dell'interfaccia [utente nelle linee guida sull'esperienza utente di Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>Architettura della tabella dei comandi di Visual Studio
Come indicato, l'architettura della tabella dei comandi supporta i principi di architettura precedenti. Di seguito sono riportati i principi di base delle astrazioni, delle strutture di dati e degli strumenti dell'architettura della tabella dei comandi:

- Sono disponibili tre tipi di elementi di base: menu, comandi e gruppi. I menu possono essere esposti nell'interfaccia utente come menu, sottomenu, barre degli strumenti o finestre degli strumenti. I comandi sono procedure che l'utente può eseguire nell'IDE, che possono essere esposte come voci di menu, pulsanti, caselle di riepilogo o altri controlli. I gruppi sono contenitori per i menu e i comandi.

- Ogni elemento viene specificato da una definizione che descrive l'elemento, la relativa priorità rispetto ad altri elementi e i flag che ne modificano il comportamento.

- Ogni elemento dispone di una posizione che descrive l'elemento padre dell'elemento. Un elemento può avere più elementi padre, in modo che possa essere visualizzato in più posizioni nell'interfaccia utente.

Ogni comando deve avere un gruppo come padre, anche se è l'unico elemento figlio in tale gruppo. Ogni menu standard deve avere anche un gruppo padre. Le barre degli strumenti e le finestre degli strumenti fungono da elementi padre. Un gruppo può avere come padre la barra dei menu principale di Visual Studio o qualsiasi menu, barra degli strumenti o finestra degli strumenti.

### <a name="how-items-are-defined"></a>Modalità di definizione degli elementi
Un file con *estensione vsct* è formattato in XML. Definisce gli elementi dell'interfaccia utente per un pacchetto e determina la posizione in cui tali elementi vengono visualizzati nell'IDE. A ogni menu, gruppo o comando del pacchetto vengono prima assegnati un GUID e un ID nella `Symbols` sezione. Nel resto del file con *estensione vsct* , ogni menu, comando e gruppo viene identificato in base alla combinazione di GUID e ID. Nell'esempio seguente viene illustrata una `Symbols` sezione tipica generata dal modello di pacchetto di Visual Studio quando nel modello è selezionato un **comando di menu** .

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

L'elemento di primo livello della `Symbols` sezione è l' [elemento GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol` gli elementi eseguono il mapping dei nomi ai GUID utilizzati dall'IDE per identificare i pacchetti e le relative parti componente.

> [!NOTE]
> I GUID vengono generati automaticamente dal modello di pacchetto di Visual Studio. È inoltre possibile creare un GUID univoco scegliendo **Crea GUID** dal menu **strumenti** .

Il primo `GuidSymbol` elemento, `guid<PackageName>Pkg` , è il GUID del pacchetto stesso. Si tratta del GUID usato da Visual Studio per caricare il pacchetto. In genere, non ha elementi figlio.

Per convenzione, i menu e i comandi sono raggruppati in un secondo `GuidSymbol` elemento, `guid<PackageName>CmdSet` , e le bitmap sono sotto un terzo `GuidSymbol` elemento, `guidImages` . Non è necessario seguire questa convenzione, ma ogni menu, gruppo, comando e bitmap deve essere figlio di un `GuidSymbol` elemento.

Nel secondo `GuidSymbol` elemento, che rappresenta il set di comandi del pacchetto, sono presenti diversi `IDSymbol` elementi. Ogni [elemento IDSymbol](../../extensibility/idsymbol-element.md) esegue il mapping di un nome a un valore numerico e può rappresentare un menu, un gruppo o un comando che fa parte del set di comandi. Gli `IDSymbol` elementi del terzo `GuidSymbol` elemento rappresentano le bitmap che possono essere usate come icone per i comandi. Poiché le coppie GUID/ID devono essere univoche in un'applicazione, due elementi figlio dello stesso `GuidSymbol` elemento potrebbero avere lo stesso valore.

### <a name="menus-groups-and-commands"></a>Menu, gruppi e comandi
Quando un menu, un gruppo o un comando ha un GUID e un ID, può essere aggiunto all'IDE. Ogni elemento dell'interfaccia utente deve avere gli elementi seguenti:

- `guid`Attributo che corrisponde al nome dell' `GuidSymbol` elemento in cui è definito l'elemento dell'interfaccia utente.

- `id`Attributo che corrisponde al nome dell' `IDSymbol` elemento associato.

Insieme, gli `guid` `id` attributi e costituiscono la *firma* dell'elemento dell'interfaccia utente.

- `priority`Attributo che determina la posizione dell'elemento dell'interfaccia utente nel menu o nel gruppo padre.

- [Elemento padre](../../extensibility/parent-element.md) con `guid` `id` attributi e che specificano la firma del menu o del gruppo padre.

#### <a name="menus"></a>Menu
Ogni menu è definito come un [elemento di menu](../../extensibility/menu-element.md) nella `Menus` sezione. I menu devono `guid` contenere `id` gli attributi, e e `priority` un `Parent` elemento e anche gli attributi e gli elementi figlio seguenti:

- `type`Attributo che specifica se il menu deve essere visualizzato nell'IDE come un tipo di menu o come barra degli strumenti.

- [Elemento Strings](../../extensibility/strings-element.md) che contiene un [elemento ButtonText](../../extensibility/buttontext-element.md), che specifica il titolo del menu nell'IDE e un [elemento CommandName](../../extensibility/commandname-element.md), che specifica il nome usato nella finestra di **comando** per accedere al menu.

- Flag facoltativi. Un [elemento CommandFlag](../../extensibility/command-flag-element.md) può essere visualizzato in una definizione di menu per modificarne l'aspetto o il comportamento nell'IDE.

Ogni `Menu` elemento deve avere un gruppo come padre, a meno che non si tratti di un elemento ancorabile, ad esempio una barra degli strumenti. Un menu ancorabile è il proprio padre. Per ulteriori informazioni sui menu e i valori per l' `type` attributo, vedere la documentazione relativa all' [elemento di menu](../../extensibility/menu-element.md) .

L'esempio seguente mostra un menu visualizzato sulla barra dei menu di Visual Studio, accanto al menu **strumenti** .

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Gruppi
Un gruppo è un elemento definito nella `Groups` sezione del file con *estensione vsct* . I gruppi sono solo contenitori. Non vengono visualizzati nell'IDE ad eccezione di una linea di divisione in un menu. Un [elemento Group](../../extensibility/group-element.md) viene pertanto definito solo in base alla firma, alla priorità e all'elemento padre.

Un gruppo può avere un menu, un altro gruppo o se stesso come elemento padre. Tuttavia, l'elemento padre è in genere un menu o una barra degli strumenti. Il menu nell'esempio precedente è un elemento figlio del `IDG_VS_MM_TOOLSADDINS` gruppo e tale gruppo è un elemento figlio della barra dei menu di Visual Studio. Il gruppo nell'esempio seguente è un elemento figlio del menu nell'esempio precedente.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Poiché fa parte di un menu, questo gruppo contiene in genere i comandi. Tuttavia, può contenere anche altri menu. Questo è il modo in cui vengono definiti i sottomenu, come illustrato nell'esempio seguente.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Comandi
Un comando fornito all'IDE viene definito come un [elemento Button](../../extensibility/button-element.md) o un [elemento combinato](../../extensibility/combo-element.md). Per essere visualizzato in un menu o in una barra degli strumenti, il comando deve avere un gruppo come padre.

##### <a name="buttons"></a>Pulsanti
I pulsanti sono definiti nella `Buttons` sezione. Qualsiasi voce di menu, pulsante o altro elemento che un utente fa clic per eseguire un singolo comando è considerato un pulsante. Alcuni tipi di pulsanti possono includere anche la funzionalità List. I pulsanti hanno gli stessi attributi obbligatori e facoltativi dei menu e possono avere anche un [elemento Icon](../../extensibility/icon-element.md) che specifica il GUID e l'ID della bitmap che rappresenta il pulsante nell'IDE. Per ulteriori informazioni sui pulsanti e sui relativi attributi, vedere la documentazione relativa all' [elemento Buttons](../../extensibility/buttons-element.md) .

Il pulsante nell'esempio seguente è un figlio del gruppo nell'esempio precedente e viene visualizzato nell'IDE come una voce di menu del menu padre del gruppo.

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

##### <a name="combos"></a>Combo
Le combinazioni combinate sono definite nella `Combos` sezione. Ogni `Combo` elemento rappresenta una casella di riepilogo a discesa nell'IDE. È possibile che la casella di riepilogo non sia scrivibile dagli utenti, a seconda del valore dell' `type` attributo della casella combinata. Le combo hanno gli stessi elementi e il comportamento dei pulsanti e possono anche avere gli attributi aggiuntivi seguenti:

- `defaultWidth`Attributo che specifica la larghezza in pixel.

- `idCommandList`Attributo che specifica un elenco contenente gli elementi visualizzati nella casella di riepilogo. L'elenco dei comandi deve essere dichiarato nello stesso `GuidSymbol` nodo che contiene la casella combinata.

Nell'esempio seguente viene definito un elemento combinato.

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
I comandi che verranno visualizzati insieme a un'icona devono includere un `Icon` elemento che fa riferimento a una bitmap usando il GUID e l'ID corrispondenti. Ogni bitmap è definita come un [elemento bitmap](../../extensibility/bitmap-element.md) nella `Bitmaps` sezione. Gli unici attributi obbligatori per una `Bitmap` definizione sono `guid` e `href` , che fa riferimento al file di origine. Se il file di origine è una striscia di risorse, è necessario anche un attributo **usato** per elencare le immagini disponibili nella striscia. Per ulteriori informazioni, vedere la documentazione relativa agli [elementi bitmap](../../extensibility/bitmap-element.md) .

### <a name="parenting"></a>Padre
Le regole seguenti determinano il modo in cui un elemento può chiamare un altro elemento come padre.

|Elemento|Definito in questa sezione della tabella dei comandi|Può essere contenuto (come un elemento padre o in base alla posizione nella `CommandPlacements` sezione o entrambi)|Può contenere (definito come padre)|
|-------------| - | - | - |
|Gruppo|[Elemento groups](../../extensibility/groups-element.md), IDE, other VSPackage|Un menu, un gruppo, l'elemento stesso|Menu, gruppi e comandi|
|Menu|[Elemento menu](../../extensibility/menus-element.md), IDE, altri VSPackage|da 1 a *n* gruppi|da 0 a *n* gruppi|
|Barra degli strumenti|[Elemento menu](../../extensibility/menus-element.md), IDE, altri VSPackage|Elemento stesso|da 0 a *n* gruppi|
|MenuItem|[Elemento Buttons](../../extensibility/buttons-element.md), IDE, other VSPackage|da 1 a *n* gruppi, l'elemento stesso|da-0 a *n* gruppi|
|Pulsante|[Elemento Buttons](../../extensibility/buttons-element.md), IDE, other VSPackage|da 1 a *n* gruppi, l'elemento stesso||
|Grafico combinato|[Elemento combos](../../extensibility/combos-element.md), IDE, altri VSPackage|da 1 a *n* gruppi, l'elemento stesso||

### <a name="menu-command-and-group-placement"></a>Selezione host per menu, comandi e gruppi
Un menu, un gruppo o un comando può essere visualizzato in più di una posizione nell'IDE. Per visualizzare un elemento in più posizioni, è necessario aggiungerlo alla `CommandPlacements` sezione come [elemento CommandPlacement](../../extensibility/commandplacement-element.md). Qualsiasi menu, gruppo o comando può essere aggiunto come posizione dei comandi. Tuttavia, le barre degli strumenti non possono essere posizionate in questo modo perché non possono apparire in più posizioni sensibili al contesto.

Le sostituzioni di comandi includono `guid` `id` attributi, e `priority` . Il GUID e l'ID devono corrispondere a quelli dell'elemento posizionato. L' `priority` attributo determina la posizione dell'elemento rispetto ad altri elementi. Quando l'IDE unisce due o più elementi con la stessa priorità, le rispettive posizioni non sono definite perché l'IDE non garantisce che le risorse del pacchetto vengano lette nello stesso ordine ogni volta che il pacchetto viene compilato.

Se un menu o un gruppo viene visualizzato in più posizioni, tutti gli elementi figlio di tale menu o gruppo verranno visualizzati in ogni istanza.

## <a name="command-visibility-and-context"></a>Visibilità e contesto del comando
Quando vengono installati più pacchetti VSPackage, un profusion di menu, voci di menu e barre degli strumenti può ingombrare l'IDE. Per evitare questo problema, è possibile controllare la visibilità dei singoli elementi dell'interfaccia utente usando *vincoli di visibilità* e flag di comando.

### <a name="visibility-constraints"></a>Vincoli di visibilità
Un vincolo di visibilità viene impostato come [elemento VisibilityItem](../../extensibility/visibilityitem-element.md) nella `VisibilityConstraints` sezione. Un vincolo di visibilità definisce contesti dell'interfaccia utente specifici in cui l'elemento di destinazione è visibile. Un menu o un comando incluso in questa sezione è visibile solo quando uno dei contesti definiti è attivo. Se in questa sezione non viene fatto riferimento a un menu o a un comando, è sempre visibile per impostazione predefinita. Questa sezione non si applica ai gruppi.

`VisibilityItem` gli elementi devono avere tre attributi, come segue: `guid` e `id` dell'elemento dell'interfaccia utente di destinazione, e `context` . L' `context` attributo specifica quando l'elemento di destinazione sarà visibile e accetta qualsiasi contesto dell'interfaccia utente valido come valore. Le costanti di contesto dell'interfaccia utente per Visual Studio sono membri della <xref:Microsoft.VisualStudio.VSConstants> classe. Ogni `VisibilityItem` elemento può assumere un solo valore di contesto. Per applicare un secondo contesto, creare un secondo `VisibilityItem` elemento che punti allo stesso elemento, come illustrato nell'esempio seguente.

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

### <a name="command-flags"></a>Flag di comando
I flag di comando seguenti possono influire sulla visibilità dei menu e dei comandi a cui si applicano.

`AlwaysCreate` Il menu viene creato anche se non contiene gruppi o pulsanti.

Valido per: `Menu`

`CommandWellOnly` Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si desidera renderlo disponibile per la personalizzazione della shell aggiuntiva, ad esempio, associarlo a una chiave. Dopo l'installazione del pacchetto VSPackage, un utente può personalizzare questi comandi aprendo la finestra di dialogo **Opzioni** e quindi modificando il posizionamento dei comandi nella categoria **ambiente tastiera** . Non influisce sulla selezione host sui menu di scelta rapida, sulle barre degli strumenti, sui controller dei menu o sui sottomenu.

Valido per: `Button` , `Combo`

`DefaultDisabled` Per impostazione predefinita, il comando viene disabilitato se il pacchetto VSPackage che implementa il comando non è caricato o se il metodo QueryStatus non è stato chiamato.

Valido per: `Button` , `Combo`

`DefaultInvisible` Per impostazione predefinita, il comando è invisibile se il pacchetto VSPackage che implementa il comando non è caricato o se il metodo QueryStatus non è stato chiamato.

Deve essere combinato con il `DynamicVisibility` flag.

Valido per: `Button` , `Combo` , `Menu`

`DynamicVisibility` È possibile modificare la visibilità del comando utilizzando il `QueryStatus` metodo o un GUID di contesto incluso nella `VisibilityConstraints` sezione.

Si applica ai comandi visualizzati nei menu, non sulle barre degli strumenti. Gli elementi della barra degli strumenti di primo livello possono essere disabilitati, ma non nascosti, quando il `OLECMDF_INVISIBLE` flag viene restituito dal `QueryStatus` metodo.

In un menu questo flag indica anche che deve essere nascosto automaticamente quando i relativi membri sono nascosti. Questo flag viene in genere assegnato ai sottomenu perché i menu di primo livello dispongono già di questo comportamento.

Deve essere combinato con il `DefaultInvisible` flag.

Valido per: `Button` , `Combo` , `Menu`

`NoShowOnMenuController` Se un comando con questo flag è posizionato in un controller di menu, il comando non viene visualizzato nell'elenco a discesa.

Valido per: `Button`

Per ulteriori informazioni sui flag di comando, vedere la documentazione dell' [elemento CommandFlag](../../extensibility/command-flag-element.md) .

#### <a name="general-requirements"></a>Requisiti generali
Il comando deve superare la serie di test seguenti prima che sia possibile visualizzarla e abilitarla:

- Il comando è posizionato correttamente.

- Il `DefaultInvisible` flag non è impostato.

- Il menu padre o la barra degli strumenti è visibile.

- Il comando non è invisibile a causa di una voce di contesto nella sezione dell' [elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .

- Il codice VSPackage che implementa l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia Visualizza e Abilita il comando. Nessun codice di interfaccia lo ha intercettato e ha agito su di esso.

- Quando un utente fa clic sul comando, diventa soggetto alla procedura illustrata nell' [algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Chiama comandi predefiniti
L' [elemento UsedCommands](../../extensibility/usedcommands-element.md) consente ai VSPackage di accedere ai comandi forniti da altri VSPackage o dall'IDE. A tale scopo, creare un [elemento UsedCommand](../../extensibility/usedcommand-element.md) con il GUID e l'ID del comando da usare. In questo modo si garantisce che il comando venga caricato da Visual Studio, anche se non fa parte della configurazione corrente di Visual Studio. Per altre informazioni, vedere [elemento UsedCommand](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Aspetto elemento interfaccia
Di seguito sono riportate alcune considerazioni per la selezione e il posizionamento degli elementi Command:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre molti elementi dell'interfaccia utente che vengono visualizzati in modo diverso a seconda della selezione host.

- Un elemento dell'interfaccia utente definito usando il `DefaultInvisible` flag non verrà visualizzato nell'IDE a meno che non sia visualizzato dall'implementazione del pacchetto VSPackage del <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodo o associato a un particolare contesto dell'interfaccia utente nella `VisibilityConstraints` sezione.

- Anche un comando posizionato correttamente potrebbe non essere visualizzato. Ciò è dovuto al fatto che l'IDE nasconde o Visualizza automaticamente alcuni comandi, a seconda delle interfacce implementate dal pacchetto VSPackage (o non è). Ad esempio, l'implementazione di un pacchetto VSPackage di alcune interfacce di compilazione fa sì che le voci di menu correlate alla compilazione vengano visualizzate automaticamente.

- `CommandWellOnly`Se si applica il flag nella definizione dell'elemento dell'interfaccia utente, il comando può essere aggiunto solo tramite personalizzazione.

- I comandi possono essere disponibili solo in alcuni contesti dell'interfaccia utente, ad esempio solo quando viene visualizzata una finestra di dialogo quando l'IDE è in visualizzazione progettazione.

- Per far sì che alcuni elementi dell'interfaccia utente vengano visualizzati nell'IDE, è necessario implementare una o più interfacce o scrivere codice.

## <a name="see-also"></a>Vedi anche
- [Estendi menu e comandi](../../extensibility/extending-menus-and-commands.md)
