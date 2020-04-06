---
title: Modalità di aggiunta di elementi dell'interfaccia utente per i pacchetti di servizi di replica di windows Documenti Microsoft
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
ms.openlocfilehash: 3b7d37bfe81c77536871248592d4a2e0734d1c62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707755"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements
Un VSPackage può aggiungere elementi dell'interfaccia utente (UI), ad esempio, menu, barre degli strumenti e finestre degli strumenti, a Visual Studio tramite il file *vsct.*

 Le linee guida di progettazione per gli elementi dell'interfaccia utente sono disponibili in Linee guida per [l'esperienza utente](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)di Visual Studio .

## <a name="the-visual-studio-command-table-architecture"></a>Architettura della tabella dei comandi di Visual StudioThe Visual Studio command table architecture
 Come indicato, l'architettura della tabella dei comandi supporta i principi dell'architettura. I principi alla base delle astrazioni, delle strutture di dati e degli strumenti dell'architettura della tabella dei comandi sono i seguenti:

- Esistono tre tipi di elementi di base: menu, comandi e gruppi. I menu possono essere esposti nell'interfaccia utente come menu, sottomenu, barre degli strumenti o finestre degli strumenti. I comandi sono procedure che l'utente può eseguire nell'IDE e possono essere esposte come voci di menu, pulsanti, caselle di riepilogo o altri controlli. I gruppi sono contenitori sia per i menu che per i comandi.

- Ogni elemento è specificato da una definizione che descrive l'elemento, la relativa priorità rispetto ad altri elementi e i flag che ne modificano il comportamento.

- Ogni elemento ha una posizione che descrive l'elemento padre dell'elemento. Un elemento può avere più elementi padre, in modo che possa essere visualizzato in più posizioni nell'interfaccia utente.

     Ogni comando deve avere un gruppo come padre, anche se è l'unico elemento figlio in tale gruppo. Ogni menu standard deve inoltre avere un gruppo padre. Le barre degli strumenti e le finestre degli strumenti fungono da genitori. Un gruppo può avere come padre la barra dei menu principale di Visual Studio o qualsiasi menu, barra degli strumenti o finestra degli strumenti.

### <a name="how-items-are-defined"></a>Modalità di definizione degli articoli
 Un file *vsct* è formattato in XML. Definisce gli elementi dell'interfaccia utente per un pacchetto e determina dove tali elementi vengono visualizzati nell'IDE. A ogni menu, gruppo o comando nel pacchetto vengono `Symbols` prima assegnati un GUID e un ID nella sezione. Nel resto del file *vsct,* ogni menu, comando e gruppo è identificato dalla combinazione GUID e ID. Nell'esempio seguente `Symbols` viene illustrata una sezione tipica generata dal modello di pacchetto di Visual Studio quando un comando di **menu** viene selezionato nel modello.

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

 L'elemento di primo `Symbols` livello della sezione è l'elemento [GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol`gli elementi eseguono il mapping dei nomi ai GUID utilizzati dall'IDE per identificare i pacchetti e le relative parti di componenti.

> [!NOTE]
> I GUID vengono generati automaticamente dal modello di pacchetto di Visual Studio.GUIDs are generated automatically by the Visual Studio package template. È inoltre possibile creare un GUID univoco scegliendo **Crea GUID** dal menu **Strumenti** .

 Il `GuidSymbol` primo `guid<PackageName>Pkg`elemento, , è il GUID del pacchetto stesso. Si tratta del GUID utilizzato da Visual Studio per caricare il pacchetto. In genere, non dispone di elementi figlio.

 Per convenzione, i menu e i `GuidSymbol` comandi `guid<PackageName>CmdSet`sono raggruppati in `GuidSymbol` un `guidImages`secondo elemento, , e le bitmap si trovano sotto un terzo elemento, . Non è necessario seguire questa convenzione, ma ogni menu, gruppo, comando `GuidSymbol` e bitmap deve essere un elemento figlio di un elemento.

 Nel secondo `GuidSymbol` elemento, che rappresenta il set `IDSymbol` di comandi del pacchetto, sono presenti diversi elementi. Ogni [elemento IDSymbol](../../extensibility/idsymbol-element.md) esegue il mapping di un nome a un valore numerico e può rappresentare un menu, un gruppo o un comando che fa parte del set di comandi. Gli `IDSymbol` elementi nel `GuidSymbol` terzo elemento rappresentano le bitmap che possono essere utilizzate come icone per i comandi. Poiché le coppie GUID/ID devono essere univoche in un'applicazione, due elementi figlio dello stesso `GuidSymbol` elemento non possono avere lo stesso valore.

### <a name="menus-groups-and-commands"></a>Menu, gruppi e comandi
 Quando un menu, gruppo o comando ha un GUID e UN ID, può essere aggiunto all'IDE. Ogni elemento dell'interfaccia utente deve avere i seguenti elementi:

- Attributo `guid` che corrisponde al `GuidSymbol` nome dell'elemento in cui è definito l'elemento dell'interfaccia utente.

- Attributo `id` che corrisponde al `IDSymbol` nome dell'elemento associato.

     Insieme, `guid` gli `id` attributi e compongono la *firma* dell'elemento dell'interfaccia utente.

- Attributo `priority` che determina la posizione dell'elemento dell'interfaccia utente nel relativo menu o gruppo padre.

- Un [elemento](../../extensibility/parent-element.md) Parent `guid` `id` con e attributi che specificano la firma del menu o del gruppo padre.

#### <a name="menus"></a>Menu
 Ogni menu è definito come `Menus` un Menu [elemento](../../extensibility/menu-element.md) nella sezione. Gli attributi `guid`, `id`e `priority` e di `Parent` menu e anche gli attributi e gli elementi aggiuntivi seguenti:

- Un `type` attributo che specifica se il menu deve essere visualizzato nell'IDE come un tipo di menu o come una barra degli strumenti.

- Un [elemento Strings](../../extensibility/strings-element.md) che contiene un elemento [ButtonText](../../extensibility/buttontext-element.md), che specifica il titolo del menu nell'IDE, e un [elemento CommandName](../../extensibility/commandname-element.md), che specifica il nome utilizzato nella finestra di **comando** per accedere al menu.

- Flag facoltativi. Un [elemento CommandFlag](../../extensibility/command-flag-element.md) può essere visualizzato in una definizione di menu per modificarne l'aspetto o il comportamento nell'IDE.

  Ogni `Menu` elemento deve avere un gruppo come padre, a meno che non si tratti di un elemento ancorabile, ad esempio una barra degli strumenti. Un menu ancorabile è il proprio elemento padre. Per ulteriori informazioni sui menu `type` e sui valori per l'attributo, vedere la documentazione dell'elemento [Menu.](../../extensibility/menu-element.md)

  Nell'esempio seguente viene illustrato un menu che viene visualizzato nella barra dei menu di Visual Studio, accanto al **strumenti** menu.

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
 Un gruppo è un elemento `Groups` definito nella sezione del file *vsct.* I gruppi sono solo contenitori. Essi non vengono visualizzati nell'IDE tranne come una linea di divisione in un menu. Pertanto, un [Group elemento](../../extensibility/group-element.md) è definito solo dalla firma, priorità e padre.

 Un gruppo può avere un menu, un altro gruppo o se stesso come padre. Tuttavia, l'elemento padre è in genere un menu o una barra degli strumenti. Il menu nell'esempio precedente è `IDG_VS_MM_TOOLSADDINS` un elemento figlio del gruppo e tale gruppo è un elemento figlio della barra dei menu di Visual Studio. Il gruppo nell'esempio seguente è un elemento figlio del menu nell'esempio precedente.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 Poiché fa parte di un menu, questo gruppo contiene in genere i comandi. Tuttavia, potrebbe contenere anche altri menu. Questo è il modo in cui vengono definiti i sottomenu, come illustrato nell'esempio seguente.

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
 Un comando fornito all'IDE è definito come elemento [Button](../../extensibility/button-element.md) o [un elemento Combo](../../extensibility/combo-element.md). Per essere visualizzato in un menu o in una barra degli strumenti, il comando deve avere un gruppo come padre.

##### <a name="buttons"></a>Pulsanti
 I pulsanti `Buttons` sono definiti nella sezione. Qualsiasi voce di menu, pulsante o altro elemento su cui un utente fa clic per eseguire un singolo comando viene considerato un pulsante. Alcuni tipi di pulsanti possono anche includere funzionalità di elenco. Pulsanti hanno gli stessi attributi obbligatori e facoltativi che i menu hanno e possono anche avere un [Icon elemento](../../extensibility/icon-element.md) che specifica il GUID e ID della bitmap che rappresenta il pulsante nell'IDE. Per altre informazioni sui pulsanti e sui relativi attributi, vedere la documentazione [dell'elemento Buttons.For](../../extensibility/buttons-element.md) more information about buttons and their attributes, see the Buttons element documentation.

 Il pulsante nell'esempio seguente è un elemento figlio del gruppo nell'esempio precedente e verrà visualizzato nell'IDE come voce di menu nel menu padre di tale gruppo.

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
 Le combinazioni sono `Combos` definite nella sezione. Ogni `Combo` elemento rappresenta una casella di riepilogo a discesa nell'IDE. La casella di riepilogo può o non può essere scrivibile `type` dagli utenti, a seconda del valore dell'attributo della combinazione. Le combinazioni hanno gli stessi elementi e lo stesso comportamento dei pulsanti e possono anche avere i seguenti attributi aggiuntivi:

- Attributo `defaultWidth` che specifica la larghezza in pixel.

- Attributo `idCommandList` che specifica un elenco contenente gli elementi visualizzati nella casella di riepilogo. L'elenco di comandi deve `GuidSymbol` essere dichiarato nello stesso nodo che contiene la combinazione.

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
 I comandi che verranno visualizzati insieme `Icon` a un'icona devono includere un elemento che fa riferimento a una bitmap utilizzando il RELATIVo GUID e ID. Ogni bitmap è definita come `Bitmaps` un Bitmap [elemento](../../extensibility/bitmap-element.md) nella sezione. Gli unici attributi `Bitmap` obbligatori `guid` per `href`una definizione sono e , che punta al file di origine. Se il file di origine è una striscia di risorse, è necessario anche un attributo **usedList** per elencare le immagini disponibili nella striscia. Per altre informazioni, vedere la documentazione [dell'elemento Bitmap.For](../../extensibility/bitmap-element.md) more information, see the Bitmap element documentation.

### <a name="parenting"></a>Genitorialità
 Le regole seguenti determinano il modo in cui un elemento può chiamare un altro elemento come elemento padre.

|Elemento|Definito in questa sezione della tabella dei comandi|Può essere contenuto (come padre, o `CommandPlacements` per posizionamento nella sezione, o entrambi)|Può contenere (indicato come padre)|
|-------------| - | - | - |
|Gruppo|[Gruppo elemento](../../extensibility/groups-element.md), l'IDE, altri VSPackage|Un menu, un gruppo, l'elemento stesso|Menu, gruppi e comandi|
|Menu|[Menus (elemento),](../../extensibility/menus-element.md)l'IDE, altri pacchetti VSPackage|da 1 a *n* gruppi|Da 0 a *n* gruppi|
|Barra degli strumenti|[Menus (elemento),](../../extensibility/menus-element.md)l'IDE, altri pacchetti VSPackage|L'elemento stesso|Da 0 a *n* gruppi|
|MenuItem|[Pulsanti elemento](../../extensibility/buttons-element.md), l'IDE, altri VSPackage|da 1 a *n* gruppi, l'elemento stesso|Da -0 a *n* gruppi|
|Pulsante|[Pulsanti elemento](../../extensibility/buttons-element.md), l'IDE, altri VSPackage|da 1 a *n* gruppi, l'elemento stesso||
|Grafico combinato|[Elemento Combos](../../extensibility/combos-element.md), idE, altri pacchetti VSPackage|da 1 a *n* gruppi, l'elemento stesso||

### <a name="menu-command-and-group-placement"></a>Posizionamento di menu, comandi e gruppi
 Un menu, un gruppo o un comando può essere visualizzato in più posizioni nell'IDE. Affinché un elemento venga visualizzato in più `CommandPlacements` posizioni, deve essere aggiunto alla sezione come [elemento CommandPlacement](../../extensibility/commandplacement-element.md). Qualsiasi menu, gruppo o comando può essere aggiunto come posizione di comando. Tuttavia, le barre degli strumenti non possono essere posizionate in questo modo perché non possono essere visualizzate in più posizioni sensibili al contesto.

 I posizionamenti `guid` `id`dei `priority` comandi hanno gli attributi , , e . Il GUID e l'ID devono corrispondere a quelli dell'elemento posizionato. L'attributo `priority` regola la posizione dell'elemento rispetto ad altri elementi. Quando l'IDE unisce due o più elementi che hanno la stessa priorità, i relativi posizionamenti non sono definiti perché l'IDE non garantisce che le risorse del pacchetto vengono lette nello stesso ordine ogni volta che viene compilato il pacchetto.

 Se un menu o un gruppo viene visualizzato in più posizioni, tutti gli elementi figlio di tale menu o gruppo verranno visualizzati in ogni istanza.

## <a name="command-visibility-and-context"></a>Visibilità e contesto dei comandi
 Quando sono installati più pacchetti VSPackage, una profusione di menu, voci di menu e barre degli strumenti può ingombrare l'IDE. Per evitare questo problema, è possibile controllare la visibilità dei singoli elementi dell'interfaccia utente utilizzando *i vincoli* di visibilità e i flag di comando.

### <a name="visibility-constraints"></a>Vincoli di visibilità
 Un vincolo di visibilità viene `VisibilityConstraints` impostato come [elemento VisibilityItem](../../extensibility/visibilityitem-element.md) nella sezione. Un vincolo di visibilità definisce contesti dell'interfaccia utente specifici in cui l'elemento di destinazione è visibile. Un menu o un comando incluso in questa sezione è visibile solo quando uno dei contesti definiti è attivo. Se in questa sezione non si fa riferimento a un menu o a un comando, questo è sempre visibile per impostazione predefinita. Questa sezione non si applica ai gruppi.

 `VisibilityItem`gli elementi devono avere tre `guid` attributi, come indicato di seguito: e `id` dell'elemento dell'interfaccia utente di destinazione e `context`. L'attributo `context` specifica quando l'elemento di destinazione sarà visibile e accetta qualsiasi contesto dell'interfaccia utente valido come valore. Le costanti di contesto dell'interfaccia <xref:Microsoft.VisualStudio.VSConstants> utente per Visual Studio sono membri della classe. Ogni `VisibilityItem` elemento può accettare un solo valore di contesto. Per applicare un secondo contesto, creare un secondo `VisibilityItem` elemento che punti allo stesso elemento, come illustrato nell'esempio seguente.

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

 `AlwaysCreate`Il menu viene creato anche se non ha gruppi o pulsanti.

 Valido per:`Menu`

 `CommandWellOnly`Applicare questo flag se il comando non viene visualizzato nel menu di primo livello e si desidera renderlo disponibile per un'ulteriore personalizzazione della shell, ad esempio associandolo a una chiave. Dopo aver installato il pacchetto VSPackage, un utente può personalizzare questi comandi aprendo la finestra di dialogo **Opzioni** e quindi modificando la posizione dei comandi nella categoria **Ambiente tastiera.** Non influisce sul posizionamento nei menu di scelta rapida, nelle barre degli strumenti, nei controller di menu o nei sottomenu.

 Valido per: `Button`,`Combo`

 `DefaultDisabled`Per impostazione predefinita, il comando è disabilitato se il pacchetto VSPackage che implementa il comando non è caricato o il QueryStatus metodo non è stato chiamato.

 Valido per: `Button`,`Combo`

 `DefaultInvisible`Per impostazione predefinita, il comando è invisibile se il pacchetto VSPackage che implementa il comando non è caricato o il QueryStatus metodo non è stato chiamato.

 Dovrebbe essere combinato `DynamicVisibility` con la bandiera.

 Valido `Button`per: `Combo`, ,`Menu`

 `DynamicVisibility`La visibilità del comando può `QueryStatus` essere modificata utilizzando il metodo `VisibilityConstraints` o un GUID di contesto incluso nella sezione.

 Si applica ai comandi visualizzati nei menu, non nelle barre degli strumenti. Gli elementi della barra degli strumenti di primo `OLECMDF_INVISIBLE` livello possono essere `QueryStatus` disabilitati, ma non nascosti, quando il flag viene restituito dal metodo.

 In un menu, questo flag indica anche che deve essere nascosto automaticamente quando i relativi membri sono nascosti. Questo flag viene in genere assegnato ai sottomenu perché i menu di primo livello hanno già questo comportamento.

 Dovrebbe essere combinato `DefaultInvisible` con la bandiera.

 Valido `Button`per: `Combo`, ,`Menu`

 `NoShowOnMenuController`Se un comando con questo flag è posizionato su un controller di menu, il comando non viene visualizzato nell'elenco a discesa.

 Valido per:`Button`

 Per altre informazioni sui flag di comando, vedere la documentazione [dell'elemento CommandFlag.For](../../extensibility/command-flag-element.md) more information about command flags, see the CommandFlag element documentation.

#### <a name="general-requirements"></a>Requisiti generali
 Il comando deve superare la seguente serie di test prima di poter essere visualizzato e abilitato:

- Il comando è posizionato correttamente.

- Il `DefaultInvisible` flag non è impostato.

- Il menu o la barra degli strumenti padre è visibile.

- Il comando non è invisibile a causa di una voce di contesto nella sezione [dell'elemento VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md)

- Il codice VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> che implementa l'interfaccia visualizza e abilita il comando. Nessun codice di interfaccia lo ha intercettato e ha agito su di esso.

- Quando un utente fa clic sul comando, questo diventa soggetto alla procedura descritta [nell'algoritmo](../../extensibility/internals/command-routing-algorithm.md)di routing .

## <a name="call-pre-defined-commands"></a>Chiamare comandi predefiniti
 Il [UsedCommands elemento](../../extensibility/usedcommands-element.md) consente a VSPackage di accedere ai comandi forniti da altri package VS o dall'IDE. A tale scopo, creare un [UsedCommand elemento](../../extensibility/usedcommand-element.md) con il GUID e ID del comando da utilizzare. In questo modo si garantisce che il comando verrà caricato da Visual Studio, anche se non fa parte della configurazione corrente di Visual Studio. Per ulteriori informazioni, vedere [Elemento UsedCommand](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Aspetto dell'elemento dell'interfaccia
 Le considerazioni per la selezione e il posizionamento degli elementi di comando sono le seguenti:Considerations for selecting and positioning command elements are as follows:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]offre molti elementi dell'interfaccia utente che vengono visualizzati in modo diverso a seconda del posizionamento.

- Un elemento dell'interfaccia utente `DefaultInvisible` definito utilizzando il flag non verrà visualizzato nell'IDE a meno <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> che non viene visualizzato dall'implementazione VSPackage del metodo o associato a un particolare contesto dell'interfaccia `VisibilityConstraints` utente nella sezione.

- Anche un comando posizionato correttamente potrebbe non essere visualizzato. Questo avviene perché l'IDE nasconde o visualizza automaticamente alcuni comandi, a seconda delle interfacce che il pacchetto VSPackage ha (o non ha) implementato. Ad esempio, l'implementazione di un vsPackage di alcune interfacce di compilazione fa sì che le voci di menu relative alla compilazione vengano visualizzate automaticamente.

- L'applicazione `CommandWellOnly` del flag nella definizione dell'elemento dell'interfaccia utente significa che il comando può essere aggiunto solo tramite personalizzazione.

- I comandi possono essere disponibili solo in determinati contesti dell'interfaccia utente, ad esempio, solo quando viene visualizzata una finestra di dialogo quando l'IDE è in visualizzazione progettazione.

- Per fare in modo che determinati elementi dell'interfaccia utente vengano visualizzati nell'IDE, è necessario implementare una o più interfacce o scrivere codice.

## <a name="see-also"></a>Vedere anche
- [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md)
