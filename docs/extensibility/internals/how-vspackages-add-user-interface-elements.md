---
title: Come i pacchetti VSPackage aggiungono Interfaccia utente elementi | Microsoft Docs
description: Informazioni su come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente, ad esempio menu, barre degli strumenti e finestre degli strumenti, Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8234183455083a05095acef1d73ad87917100660
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626130"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente
Un VSPackage può aggiungere elementi dell'interfaccia utente, ad esempio menu, barre degli strumenti e finestre degli strumenti, per Visual Studio tramite il file con estensione *vsct.*

Le linee guida di progettazione per gli elementi dell'interfaccia utente sono [Visual Studio linee guida per l'esperienza utente.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="the-visual-studio-command-table-architecture"></a>Architettura Visual Studio tabella dei comandi
Come si può vedere, l'architettura della tabella dei comandi supporta i principi dell'architettura. I tenets alla base delle astrazioni, delle strutture dei dati e degli strumenti dell'architettura della tabella dei comandi sono i seguenti:

- Esistono tre tipi di elementi di base: menu, comandi e gruppi. I menu possono essere esposti nell'interfaccia utente come menu, sottomenu, barre degli strumenti o finestre degli strumenti. I comandi sono procedure che l'utente può eseguire nell'IDE e possono essere esposti come voci di menu, pulsanti, caselle di riepilogo o altri controlli. I gruppi sono contenitori per menu e comandi.

- Ogni elemento viene specificato da una definizione che descrive l'elemento, la relativa priorità rispetto ad altri elementi e i flag che ne modificano il comportamento.

- Ogni elemento ha una posizione che descrive l'elemento padre dell'elemento. Un elemento può avere più elementi padre, in modo che possa essere visualizzato in più posizioni nell'interfaccia utente.

Ogni comando deve avere un gruppo come padre, anche se è l'unico figlio in tale gruppo. Ogni menu standard deve avere anche un gruppo padre. Le barre degli strumenti e le finestre degli strumenti fungono da elementi padre. Un gruppo può avere come padre la barra Visual Studio menu principale o qualsiasi menu, barra degli strumenti o finestra degli strumenti.

### <a name="how-items-are-defined"></a>Modalità di definizione degli elementi
Un file *con estensione vsct* è formattato in XML. Definisce gli elementi dell'interfaccia utente per un pacchetto e determina la posizione in cui tali elementi vengono visualizzati nell'IDE. A ogni menu, gruppo o comando nel pacchetto vengono innanzitutto assegnati un GUID e un ID nella `Symbols` sezione . Nel resto del file *vsct,* ogni menu, comando e gruppo è identificato dalla combinazione di GUID e ID. Nell'esempio seguente viene illustrata una sezione tipica generata dal modello Visual Studio pacchetto quando nel modello è selezionato un comando `Symbols` di menu. 

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

L'elemento di primo livello della `Symbols` sezione è [l'elemento GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol` I nomi degli elementi vengono mappati ai GUID usati dall'IDE per identificare i pacchetti e le relative parti del componente.

> [!NOTE]
> I GUID vengono generati automaticamente dal modello Visual Studio pacchetto. È anche possibile creare un GUID univoco scegliendo **Crea GUID** **dal** menu Strumenti.

Il primo `GuidSymbol` elemento, `guid<PackageName>Pkg` , è il GUID del pacchetto stesso. Si tratta del GUID usato dal Visual Studio per caricare il pacchetto. In genere, non dispone di elementi figlio.

Per convenzione, i menu e i comandi sono raggruppati sotto un secondo elemento, e le bitmap si `GuidSymbol` `guid<PackageName>CmdSet` esere sotto un terzo `GuidSymbol` elemento, `guidImages` . Non è necessario seguire questa convenzione, ma ogni menu, gruppo, comando e bitmap deve essere figlio di un `GuidSymbol` elemento.

Nel secondo `GuidSymbol` elemento, che rappresenta il set di comandi del pacchetto, sono presenti diversi `IDSymbol` elementi. Ogni [elemento IDSymbol](../../extensibility/idsymbol-element.md) esegue il mapping di un nome a un valore numerico e può rappresentare un menu, un gruppo o un comando che fa parte del set di comandi. Gli `IDSymbol` elementi nel terzo elemento rappresentano bitmap che possono essere usate come icone per i `GuidSymbol` comandi. Poiché le coppie GUID/ID devono essere univoche in un'applicazione, nessun elemento figlio dello stesso elemento `GuidSymbol` può avere lo stesso valore.

### <a name="menus-groups-and-commands"></a>Menu, gruppi e comandi
Quando un menu, un gruppo o un comando ha un GUID e un ID, può essere aggiunto all'IDE. Ogni elemento dell'interfaccia utente deve avere gli elementi seguenti:

- Attributo `guid` che corrisponde al nome dell'elemento in cui è definito `GuidSymbol` l'elemento dell'interfaccia utente.

- Attributo `id` che corrisponde al nome dell'elemento `IDSymbol` associato.

Insieme, gli `guid` attributi e costituiscono la firma `id` *dell'elemento* dell'interfaccia utente.

- Attributo `priority` che determina la posizione dell'elemento dell'interfaccia utente nel menu o nel gruppo padre.

- Elemento [Parent con](../../extensibility/parent-element.md) attributi e che `guid` `id` specificano la firma del menu o del gruppo padre.

#### <a name="menus"></a>Menu
Ogni menu è definito come elemento [Menu](../../extensibility/menu-element.md) nella `Menus` sezione . I menu devono avere attributi , e e un elemento e anche `guid` gli attributi e gli elementi figlio aggiuntivi `id` `priority` `Parent` seguenti:

- Attributo che specifica se il menu deve essere visualizzato nell'IDE come tipo `type` di menu o come barra degli strumenti.

- Elemento [Strings](../../extensibility/strings-element.md) che contiene un [elemento ButtonText](../../extensibility/buttontext-element.md), che specifica il titolo del menu nell'IDE, e un  elemento [CommandName](../../extensibility/commandname-element.md), che specifica il nome utilizzato nella finestra di comando per accedere al menu.

- Flag facoltativi. Un [elemento CommandFlag può](../../extensibility/command-flag-element.md) essere visualizzato in una definizione di menu per modificarne l'aspetto o il comportamento nell'IDE.

Ogni elemento deve avere un gruppo come padre, a meno che non sia un elemento `Menu` ancorabile, ad esempio una barra degli strumenti. Un menu ancorabile è il proprio elemento padre. Per altre informazioni sui menu e sui valori per `type` l'attributo, vedere la documentazione [dell'elemento Menu.](../../extensibility/menu-element.md)

L'esempio seguente mostra un menu visualizzato nella barra Visual Studio menu, accanto **al** menu Strumenti.

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
Un gruppo è un elemento definito nella `Groups` sezione del file con estensione *vsct.* I gruppi sono solo contenitori. Non vengono visualizzate nell'IDE se non come linea di divisione in un menu. Pertanto, un [elemento Group](../../extensibility/group-element.md) viene definito solo dalla firma, dalla priorità e dall'elemento padre.

Un gruppo può avere un menu, un altro gruppo o se stesso come padre. Tuttavia, l'elemento padre è in genere un menu o una barra degli strumenti. Il menu nell'esempio precedente è un elemento figlio del gruppo e tale gruppo è un elemento figlio della barra Visual Studio `IDG_VS_MM_TOOLSADDINS` menu. Il gruppo nell'esempio seguente è un elemento figlio del menu nell'esempio precedente.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Poiché fa parte di un menu, questo gruppo contiene in genere comandi. Tuttavia, potrebbe contenere anche altri menu. In questo modo vengono definiti i sottomenu, come illustrato nell'esempio seguente.

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
Un comando fornito all'IDE è definito come elemento [Button](../../extensibility/button-element.md) o [Combo.](../../extensibility/combo-element.md) Per essere visualizzato in un menu o in una barra degli strumenti, il comando deve avere un gruppo come padre.

##### <a name="buttons"></a>Pulsanti
I pulsanti sono definiti nella `Buttons` sezione . Qualsiasi voce di menu, pulsante o altro elemento su cui un utente fa clic per eseguire un singolo comando viene considerato un pulsante. Alcuni tipi di pulsante possono includere anche funzionalità di elenco. I pulsanti hanno gli stessi attributi obbligatori e facoltativi dei menu e possono anche avere un elemento [Icon](../../extensibility/icon-element.md) che specifica il GUID e l'ID della bitmap che rappresenta il pulsante nell'IDE. Per altre informazioni sui pulsanti e sui relativi attributi, vedere la documentazione [dell'elemento Buttons.](../../extensibility/buttons-element.md)

Il pulsante nell'esempio seguente è un elemento figlio del gruppo nell'esempio precedente e viene visualizzato nell'IDE come voce di menu nel menu padre del gruppo.

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
Le combinazioni sono definite nella `Combos` sezione . Ogni `Combo` elemento rappresenta una casella di riepilogo a discesa nell'IDE. La casella di riepilogo può essere scrivibile o meno dagli utenti, a seconda del valore `type` dell'attributo della combinazione. Le combinazioni hanno gli stessi elementi e gli stessi comportamenti dei pulsanti e possono avere anche gli attributi aggiuntivi seguenti:

- Attributo `defaultWidth` che specifica la larghezza in pixel.

- Attributo `idCommandList` che specifica un elenco contenente gli elementi visualizzati nella casella di riepilogo. L'elenco di comandi deve essere dichiarato nello stesso `GuidSymbol` nodo che contiene la combinazione.

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
I comandi che verranno visualizzati insieme a un'icona devono includere un elemento che fa riferimento `Icon` a una bitmap usando il RELATIVO GUID e ID. Ogni bitmap è definita come [elemento Bitmap](../../extensibility/bitmap-element.md) nella `Bitmaps` sezione . Gli unici attributi obbligatori per una `Bitmap` definizione sono e , che punta al file di `guid` `href` origine. Se il file di origine è una striscia di risorse, è necessario anche un **attributo usedList** per elencare le immagini disponibili nella striscia. Per altre informazioni, vedere la documentazione [dell'elemento Bitmap.](../../extensibility/bitmap-element.md)

### <a name="parenting"></a>Genitorialità
Le regole seguenti regolano il modo in cui un elemento può chiamare un altro elemento come padre.

|Elemento|Definito in questa sezione della tabella dei comandi|Può essere contenuto (come elemento padre, in base al posizionamento nella `CommandPlacements` sezione o a entrambi)|Può contenere (definito padre)|
|-------------| - | - | - |
|Group|[Elemento Groups](../../extensibility/groups-element.md), IDE, altri VSPackage|Un menu, un gruppo, l'elemento stesso|Menu, gruppi e comandi|
|Menu|[Elemento Menus](../../extensibility/menus-element.md), IDE, altri VSPackage|Da 1 a *n* gruppi|Da 0 a *n* gruppi|
|Barra degli strumenti|[Elemento Menus](../../extensibility/menus-element.md), IDE, altri VSPackage|L'elemento stesso|Da 0 a *n* gruppi|
|MenuItem|[Elemento Buttons](../../extensibility/buttons-element.md), IDE, altri VSPackage|Da 1 *a n* gruppi, l'elemento stesso|Da -0 a *n* gruppi|
|Button|[Elemento Buttons](../../extensibility/buttons-element.md), IDE, altri VSPackage|Da 1 *a n* gruppi, l'elemento stesso||
|Grafico combinato|[Elemento Combos](../../extensibility/combos-element.md), IDE, altri VSPackage|Da 1 *a n* gruppi, l'elemento stesso||

### <a name="menu-command-and-group-placement"></a>Posizionamento di menu, comandi e gruppi
Un menu, un gruppo o un comando può essere visualizzato in più di una posizione nell'IDE. Per visualizzare un elemento in più posizioni, è necessario aggiungere alla sezione `CommandPlacements` come elemento [CommandPlacement](../../extensibility/commandplacement-element.md). Qualsiasi menu, gruppo o comando può essere aggiunto come posizionamento dei comandi. Tuttavia, le barre degli strumenti non possono essere posizionate in questo modo perché non possono essere visualizzate in più posizioni sensibili al contesto.

Le posizioni dei comandi `guid` hanno attributi , e `id` `priority` . Il GUID e l'ID devono corrispondere a quelli dell'elemento posizionato. `priority`L'attributo determina la posizione dell'elemento rispetto ad altri elementi. Quando l'IDE unisce due o più elementi con la stessa priorità, i relativi posizionamenti non sono definiti perché l'IDE non garantisce che le risorse del pacchetto siano lette nello stesso ordine ogni volta che viene compilato il pacchetto.

Se un menu o un gruppo viene visualizzato in più posizioni, tutti gli elementi figlio del menu o del gruppo verranno visualizzati in ogni istanza.

## <a name="command-visibility-and-context"></a>Visibilità e contesto dei comandi
Quando vengono installati più VSPackage, una grande di menu, voci di menu e barre degli strumenti può creare confusione nell'IDE. Per evitare questo problema, è possibile controllare la visibilità dei singoli elementi dell'interfaccia utente usando vincoli *di visibilità* e flag di comando.

### <a name="visibility-constraints"></a>Vincoli di visibilità
Un vincolo di visibilità viene impostato come [elemento VisibilityItem](../../extensibility/visibilityitem-element.md) nella `VisibilityConstraints` sezione . Un vincolo di visibilità definisce contesti dell'interfaccia utente specifici in cui l'elemento di destinazione è visibile. Un menu o un comando incluso in questa sezione è visibile solo quando è attivo uno dei contesti definiti. Se in questa sezione non viene fatto riferimento a un menu o a un comando, è sempre visibile per impostazione predefinita. Questa sezione non si applica ai gruppi.

`VisibilityItem` Gli elementi devono avere tre attributi, come indicato di seguito: `guid` e `id` dell'elemento dell'interfaccia utente di destinazione e `context` . `context`L'attributo specifica quando l'elemento di destinazione sarà visibile e accetta qualsiasi contesto dell'interfaccia utente valido come valore. Le costanti di contesto dell'interfaccia Visual Studio sono membri della <xref:Microsoft.VisualStudio.VSConstants> classe . Ogni `VisibilityItem` elemento può assumere un solo valore di contesto. Per applicare un secondo contesto, creare un secondo `VisibilityItem` elemento che punti allo stesso elemento, come illustrato nell'esempio seguente.

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

`CommandWellOnly` Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si vuole renderlo disponibile per la personalizzazione aggiuntiva della shell, ad esempio associarlo a una chiave. Dopo l'installazione di VSPackage, un utente  può personalizzare questi comandi aprendo la finestra di dialogo Opzioni e quindi modificando il posizionamento dei comandi nella **categoria Ambiente tastiera.** Non influisce sulla posizione in menu di scelta rapida, barre degli strumenti, controller di menu o sottomenu.

Valido per: `Button` , `Combo`

`DefaultDisabled` Per impostazione predefinita, il comando è disabilitato se il pacchetto VSPackage che implementa il comando non viene caricato o il metodo QueryStatus non è stato chiamato.

Valido per: `Button` , `Combo`

`DefaultInvisible` Per impostazione predefinita, il comando è invisibile se il pacchetto VSPackage che implementa il comando non viene caricato o il metodo QueryStatus non è stato chiamato.

Deve essere combinato con il `DynamicVisibility` flag .

Valido per: `Button` , `Combo` , `Menu`

`DynamicVisibility` La visibilità del comando può essere modificata usando il metodo o un GUID di contesto `QueryStatus` incluso nella `VisibilityConstraints` sezione .

Si applica ai comandi visualizzati nei menu, non nelle barre degli strumenti. Gli elementi della barra degli strumenti di primo livello possono essere disabilitati, ma non nascosti, quando il `OLECMDF_INVISIBLE` flag viene restituito dal `QueryStatus` metodo .

In un menu, questo flag indica anche che deve essere nascosto automaticamente quando i relativi membri sono nascosti. Questo flag viene in genere assegnato ai sottomenu perché i menu di primo livello hanno già questo comportamento.

Deve essere combinato con il `DefaultInvisible` flag .

Valido per: `Button` , `Combo` , `Menu`

`NoShowOnMenuController` Se un comando con questo flag è posizionato in un controller di menu, il comando non viene visualizzato nell'elenco a discesa.

Valido per: `Button`

Per altre informazioni sui flag di comando, vedere la documentazione [dell'elemento CommandFlag.](../../extensibility/command-flag-element.md)

#### <a name="general-requirements"></a>Requisiti generali
Per poter essere visualizzato e abilitato, il comando deve superare la serie di test seguente:

- Il comando è posizionato correttamente.

- Il `DefaultInvisible` flag non è impostato.

- Il menu o la barra degli strumenti padre è visibile.

- Il comando non è invisibile a causa di una voce di contesto nella [sezione dell'elemento VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md)

- Il codice VSPackage che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia visualizza e abilita il comando. Nessun codice di interfaccia l'ha intercettata e ha agisce su di essa.

- Quando un utente fa clic sul comando, diventa soggetto alla procedura descritta in [Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Chiamare comandi predefiniti
[L'elemento UsedCommands](../../extensibility/usedcommands-element.md) consente ai vspackage di accedere ai comandi forniti da altri VSPackage o dall'IDE. A tale scopo, creare un [elemento UsedCommand](../../extensibility/usedcommand-element.md) con il GUID e l'ID del comando da usare. Ciò garantisce che il comando verrà caricato da Visual Studio, anche se non fa parte della configurazione Visual Studio corrente. Per altre informazioni, vedere [Elemento UsedCommand](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Aspetto degli elementi dell'interfaccia
Le considerazioni per la selezione e il posizionamento degli elementi di comando sono le seguenti:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre molti elementi dell'interfaccia utente che vengono visualizzati in modo diverso a seconda della posizione.

- Un elemento dell'interfaccia utente definito tramite il flag non verrà visualizzato nell'IDE a meno che non venga visualizzato dall'implementazione VSPackage del metodo o associato a un particolare contesto dell'interfaccia utente nella `DefaultInvisible` <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> sezione `VisibilityConstraints` .

- Anche un comando posizionato correttamente potrebbe non essere visualizzato. Ciò è dovuto al fatto che l'IDE nasconde o visualizza automaticamente alcuni comandi, a seconda delle interfacce implementate dal pacchetto VSPackage o meno. Ad esempio, l'implementazione di un VSPackage di alcune interfacce di compilazione fa sì che le voci di menu correlate alla compilazione siano visualizzate automaticamente.

- L'applicazione del `CommandWellOnly` flag nella definizione dell'elemento dell'interfaccia utente significa che il comando può essere aggiunto solo tramite personalizzazione.

- I comandi possono essere disponibili solo in determinati contesti dell'interfaccia utente, ad esempio solo quando viene visualizzata una finestra di dialogo quando l'IDE è in visualizzazione Progettazione.

- Per visualizzare determinati elementi dell'interfaccia utente nell'IDE, è necessario implementare una o più interfacce o scrivere codice.

## <a name="see-also"></a>Vedi anche
- [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md)
