---
title: Authoring. File vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82960de02c43a7c4002e189d573a914bb2a73f20
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186662"
---
# <a name="author-vsct-files"></a>Crea file con estensione vsct
Questo documento illustra come creare un file con *estensione vsct* per aggiungere voci di menu, barre degli strumenti e altri elementi dell'interfaccia utente a Visual Studio Integrated Development Environment (IDE). Usare questi passaggi quando si aggiungono elementi dell'interfaccia utente a un pacchetto di Visual Studio (VSPackage) che non dispone già di un file con *estensione vsct* .

 Per i nuovi progetti, è consigliabile usare il modello di pacchetto di Visual Studio perché genera un file con *estensione vsct* che, a seconda delle selezioni, dispone già degli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato. È possibile modificare il file con *estensione vsct* per soddisfare i requisiti del pacchetto VSPackage. Per ulteriori informazioni su come modificare un file con estensione *vsct* , vedere gli esempi in [estendere i menu e i comandi](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Creare il file
 Creazione di un file con *estensione vsct* in queste fasi: creare la struttura per file e risorse, dichiarare gli elementi dell'interfaccia utente, inserire gli elementi dell'interfaccia utente nell'IDE e aggiungere eventuali comportamenti specializzati.

### <a name="file-structure"></a>Struttura di file
 La struttura di base di un file con *estensione vsct* è un elemento radice [CommandTable](../../extensibility/commandtable-element.md) che contiene un elemento [Commands](../../extensibility/commands-element.md) e un elemento [symbols](../../extensibility/symbols-element.md) .

#### <a name="to-create-the-file-structure"></a>Per creare la struttura di file

1. Aggiungere un file con *estensione vsct* al progetto seguendo i passaggi in [procedura: creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Aggiungere gli spazi dei nomi richiesti all'elemento `CommandTable`, come illustrato nell'esempio seguente:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Nell'elemento `CommandTable` aggiungere un elemento `Commands` per ospitare tutti i menu, le barre degli strumenti, i gruppi di comandi e i comandi personalizzati. Per poter caricare gli elementi dell'interfaccia utente personalizzati, è necessario che l'attributo `Package` dell'elemento `Commands` sia impostato sul nome del pacchetto.

     Dopo l'elemento `Commands`, aggiungere un elemento `Symbols` per definire i GUID per il pacchetto e i nomi e gli ID di comando per gli elementi dell'interfaccia utente.

### <a name="include-visual-studio-resources"></a>Includi risorse di Visual Studio
 Usare l'elemento [extern](../../extensibility/extern-element.md) per accedere ai file che definiscono i comandi di Visual Studio e i menu necessari per inserire gli elementi dell'interfaccia utente nell'IDE. Se si utilizzeranno comandi definiti all'esterno del pacchetto, usare l'elemento [UsedCommands](../../extensibility/usedcommands-element.md) per informare Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Per includere le risorse di Visual Studio

1. Nella parte superiore dell'elemento `CommandTable` aggiungere un `Extern` elemento per ogni file esterno a cui fare riferimento e impostare l'attributo `href` sul nome del file. Per accedere alle risorse di Visual Studio, è possibile fare riferimento ai file di intestazione seguenti:

   - *Stdidcmd. h*: definisce gli ID per tutti i comandi esposti da Visual Studio.

   - *Vsshlids. h*: contiene gli ID comando per i menu di Visual Studio.

2. Se il pacchetto chiama qualsiasi comando definito da Visual Studio o da altri pacchetti, aggiungere un elemento `UsedCommands` dopo l'elemento `Commands`. Popolare questo elemento con un elemento [UsedCommand](../../extensibility/usedcommand-element.md) per ogni comando chiamato che non fa parte del pacchetto. Impostare gli attributi `guid` e `id` degli elementi `UsedCommand` sui valori GUID e ID dei comandi da chiamare.

   Per altre informazioni su come trovare i GUID e gli ID dei comandi di Visual Studio, vedere [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Per chiamare comandi da altri pacchetti, usare il GUID e l'ID del comando come definito nel file con *estensione vsct* per tali pacchetti.

### <a name="declare-ui-elements"></a>Dichiara elementi dell'interfaccia utente
 Dichiarare tutti i nuovi elementi dell'interfaccia utente nella sezione `Symbols` del file con *estensione vsct* .

#### <a name="to-declare-ui-elements"></a>Per dichiarare gli elementi dell'interfaccia utente

1. Nell'elemento `Symbols` aggiungere tre elementi [GuidSymbol](../../extensibility/guidsymbol-element.md) . Ogni elemento `GuidSymbol` dispone di un attributo `name` e di un `value` attributo. Impostare l'attributo `name` in modo che rispecchi lo scopo dell'elemento. L'attributo `value` accetta un GUID. Per generare un GUID, scegliere **Crea GUID**dal menu **strumenti** e quindi selezionare **formato registro di sistema**.

     Il primo elemento `GuidSymbol` rappresenta il pacchetto e in genere non dispone di elementi figlio. Il secondo elemento `GuidSymbol` rappresenta il set di comandi e conterrà tutti i simboli che definiscono i menu, i gruppi e i comandi. Il terzo elemento `GuidSymbol` rappresenta l'archivio immagini e contiene i simboli per tutte le icone per i comandi. Se non si dispone di comandi che usano icone, è possibile omettere il terzo elemento `GuidSymbol`.

2. Nell'elemento `GuidSymbol` che rappresenta il set di comandi aggiungere uno o più elementi [IDSymbol](../../extensibility/idsymbol-element.md) . Ognuno di questi rappresenta un menu, una barra degli strumenti, un gruppo o un comando che si sta aggiungendo all'interfaccia utente.

     Per ogni elemento `IDSymbol`, impostare l'attributo `name` sul nome che verrà usato per fare riferimento al menu, al gruppo o al comando corrispondente, quindi impostare l'elemento `value` su un numero esadecimale che rappresenterà l'ID di comando. Due elementi `IDSymbol` con lo stesso elemento padre possono avere lo stesso valore.

3. Se uno degli elementi dell'interfaccia utente richiede icone, aggiungere un elemento `IDSymbol` per ogni icona all'elemento `GuidSymbol` che rappresenta l'archivio immagini.

### <a name="put-ui-elements-in-the-ide"></a>Inserire gli elementi dell'interfaccia utente nell'IDE
 Gli elementi [menu](../../extensibility/menus-element.md), [gruppi](../../extensibility/groups-element.md)e [pulsanti](../../extensibility/buttons-element.md) contengono le definizioni per tutti i menu, i gruppi e i comandi definiti nel pacchetto. Inserire i menu, i gruppi e i comandi nell'IDE usando un elemento [padre](../../extensibility/parent-element.md) , che fa parte della definizione dell'elemento dell'interfaccia utente, oppure usando un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) definito altrove.

 Ogni elemento `Menu`, `Group`e `Button` ha un attributo `guid` e un attributo `id`. Impostare sempre l'attributo `guid` in modo che corrisponda al nome dell'elemento `GuidSymbol` che rappresenta il set di comandi e impostare l'attributo `id` sul nome dell'elemento `IDSymbol` che rappresenta il menu, il gruppo o il comando nella sezione `Symbols`.

#### <a name="to-define-ui-elements"></a>Per definire gli elementi dell'interfaccia utente

1. Se si definiscono i nuovi menu, i sottomenu, i menu di scelta rapida o le barre degli strumenti, aggiungere un elemento `Menus` all'elemento `Commands`. Quindi, per ogni menu da creare, aggiungere un elemento di [menu](../../extensibility/menu-element.md) all'elemento `Menus`.

    Impostare gli attributi `guid` e `id` dell'elemento `Menu`, quindi impostare l'attributo `type` sul tipo di menu desiderato. È anche possibile impostare l'attributo `priority` per stabilire la posizione relativa del menu nel gruppo padre.

   > [!NOTE]
   > L'attributo `priority` non è valido per le barre degli strumenti e i menu di scelta rapida.

2. Tutti i comandi nell'IDE di Visual Studio devono essere ospitati da gruppi di comandi, che sono gli elementi figlio diretti di menu e barre degli strumenti. Se si aggiungono nuovi menu o barre degli strumenti all'IDE, questi devono contenere nuovi gruppi di comandi. È inoltre possibile aggiungere gruppi di comandi a menu e barre degli strumenti esistenti in modo da raggruppare visivamente i comandi.

    Quando si aggiungono nuovi gruppi di comandi, è necessario innanzitutto creare un elemento `Groups`, quindi aggiungervi un elemento [Group](../../extensibility/group-element.md) per ogni gruppo di comandi.

    Impostare gli attributi `guid` e `id` di ogni elemento `Group`, quindi impostare l'attributo `priority` per stabilire la posizione relativa del gruppo nel menu padre. Per altre informazioni, vedere [creare gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Se si aggiungono nuovi comandi all'IDE, aggiungere un elemento `Buttons` all'elemento `Commands`. Quindi, per ogni comando aggiungere un elemento [Button](../../extensibility/button-element.md) all'elemento `Buttons`.

   1. Impostare gli attributi `guid` e `id` di ogni elemento `Button`, quindi impostare l'attributo `type` sul tipo di pulsante desiderato. È anche possibile impostare l'attributo `priority` per stabilire la posizione relativa del comando nel gruppo padre.

       > [!NOTE]
       > Utilizzare `type="button"` per i comandi di menu standard e i pulsanti sulle barre degli strumenti.

   2. Nell'elemento `Button` aggiungere un elemento [Strings](../../extensibility/strings-element.md) che contiene un elemento [ButtonText](../../extensibility/buttontext-element.md) e un elemento [CommandName](../../extensibility/commandname-element.md) . L'elemento `ButtonText` fornisce l'etichetta di testo per una voce di menu o la descrizione comando per un pulsante della barra degli strumenti. L'elemento `CommandName` fornisce il nome del comando da usare nell'area dei comandi.

   3. Se il comando avrà un'icona, creare un elemento [Icon](../../extensibility/icon-element.md) nell'elemento `Button` e impostare i relativi attributi `guid` e `id` sull'elemento `Bitmap` per l'icona.

       > [!NOTE]
       > I pulsanti della barra degli strumenti devono avere icone.

   Per ulteriori informazioni, vedere [oggetti MenuCommand e OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Se uno dei comandi richiede icone, aggiungere un elemento [bitmap](../../extensibility/bitmaps-element.md) all'elemento `Commands`. Quindi, per ogni icona aggiungere un elemento [bitmap](../../extensibility/bitmap-element.md) all'elemento `Bitmaps`. Qui è possibile specificare il percorso della risorsa bitmap. Per altre informazioni, vedere [aggiungere icone ai comandi di menu](../../extensibility/adding-icons-to-menu-commands.md).

   È possibile fare affidamento sulla struttura padre per inserire correttamente la maggior parte dei menu, dei gruppi e dei comandi. Per i set di comandi di grandi dimensioni o quando un menu, un gruppo o un comando deve essere visualizzato in più posizioni, è consigliabile specificare la posizione dei comandi.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Per fare affidamento sull'elemento padre per inserire gli elementi dell'interfaccia utente nell'IDE

1. Per i tipici elementi padre, creare un elemento `Parent` in ogni elemento `Menu`, `Group`e `Command` definito nel pacchetto.

    La destinazione dell'elemento `Parent` è il menu o il gruppo che conterrà il menu, il gruppo o il comando.

   1. Impostare l'attributo `guid` sul nome dell'elemento `GuidSymbol` che definisce il set di comandi. Se l'elemento di destinazione non fa parte del pacchetto, usare il GUID per tale set di comandi, come definito nel file con *estensione vsct* corrispondente.

   2. Impostare l'attributo `id` in modo che corrisponda all'attributo `id` del menu o del gruppo di destinazione. Per un elenco dei menu e dei gruppi esposti da Visual Studio, vedere [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Se si dispone di un numero elevato di elementi dell'interfaccia utente da inserire nell'IDE o se si dispone di elementi che devono essere visualizzati in più punti, definirne le posizioni nell'elemento [CommandPlacements](../../extensibility/commandplacements-element.md) , come illustrato nei passaggi seguenti.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Per utilizzare la posizione dei comandi per posizionare gli elementi dell'interfaccia utente nell'IDE

1. Dopo l'elemento `Commands`, aggiungere un elemento `CommandPlacements`.

2. Nell'elemento `CommandPlacements` aggiungere un elemento `CommandPlacement` per ogni menu, gruppo o comando da inserire.

    Ogni elemento `CommandPlacement` o elemento `Parent` inserisce un menu, un gruppo o un comando in una posizione IDE. Un elemento dell'interfaccia utente può avere un solo padre, ma può avere più posizionamenti dei comandi. Per inserire un elemento dell'interfaccia utente in più posizioni, aggiungere un `CommandPlacement` elemento per ogni posizione.

3. Impostare gli attributi `guid` e `id` di ogni elemento `CommandPlacement` sul menu o sul gruppo host, esattamente come per un elemento `Parent`. È anche possibile impostare l'attributo `priority` per stabilire la posizione relativa dell'elemento dell'interfaccia utente.

   È possibile combinare la selezione host in base al padre e al posizionamento dei comandi. Tuttavia, per i set di comandi di grandi dimensioni, è consigliabile usare solo la posizione dei comandi.

### <a name="add-specialized-behaviors"></a>Aggiungere comportamenti specializzati
 È possibile utilizzare l'elemento [CommandFlag](../../extensibility/command-flag-element.md) per modificare il comportamento di menu e comandi, ad esempio per modificarne l'aspetto e la visibilità. È anche possibile influenzare quando un comando è visibile usando l'elemento [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) o aggiungere tasti di scelta rapida [usando l'elemento tasti di](../../extensibility/keybindings-element.md) scelta rapida. Alcuni tipi di menu e comandi dispongono già di comportamenti specializzati incorporati.

#### <a name="to-add-specialized-behaviors"></a>Per aggiungere comportamenti specializzati

1. Per rendere visibile un elemento dell'interfaccia utente solo in alcuni contesti dell'interfaccia utente, ad esempio quando viene caricata una soluzione, usare vincoli di visibilità.

   1. Dopo l'elemento `Commands`, aggiungere un elemento `VisibilityConstraints`.

   2. Per ogni elemento dell'interfaccia utente da vincolare, aggiungere un elemento [VisibilityItem](../../extensibility/visibilityitem-element.md) .

   3. Per ogni elemento `VisibilityItem`, impostare gli attributi `guid` e `id` sul menu, il gruppo o il comando, quindi impostare l'attributo `context` sul contesto dell'interfaccia utente desiderato, come definito nella classe <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>.

2. Per impostare la visibilità o la disponibilità di un elemento dell'interfaccia utente nel codice, usare uno o più dei flag di comando seguenti:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Per ulteriori informazioni, vedere l'elemento [CommandFlag](../../extensibility/command-flag-element.md) .

3. Per modificare il modo in cui viene visualizzato un elemento o modificarne l'aspetto in modo dinamico, usare uno o più dei flag di comando seguenti:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Per ulteriori informazioni, vedere l'elemento [CommandFlag](../../extensibility/command-flag-element.md) .

4. Per modificare il modo in cui un elemento reagisce quando riceve i comandi, usare uno o più dei flag di comando seguenti:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Per ulteriori informazioni, vedere l'elemento [CommandFlag](../../extensibility/command-flag-element.md) .

5. Per alleghi un tasto di scelta rapida dipendente dal menu a un menu o a un elemento in un menu, aggiungere un carattere e commerciale (&) nell'elemento `ButtonText` per il menu o la voce di menu. Il carattere che segue la e commerciale è il tasto di scelta rapida attivo quando il menu padre è aperto.

6. Per associare un tasto di scelta rapida indipendente dal menu a un comando, [usare l'elemento tasti di](../../extensibility/keybindings-element.md) scelta rapida. Per ulteriori informazioni, vedere l'elemento di [associazione di tasti](../../extensibility/keybinding-element.md) .

7. Per localizzare il testo del menu, usare l'elemento `LocCanonicalName`. Per ulteriori informazioni, vedere l'elemento [Strings](../../extensibility/strings-element.md) .

   Alcuni tipi di menu e pulsanti includono comportamenti specializzati. Nell'elenco seguente vengono descritti alcuni tipi di menu e pulsanti specializzati. Per altri tipi, vedere le descrizioni degli attributi `types` nel [menu](../../extensibility/menu-element.md), nel [pulsante](../../extensibility/button-element.md)e negli elementi [combinati](../../extensibility/combo-element.md) .

   - Casella combinata: una casella combinata è un elenco a discesa che può essere usato su una barra degli strumenti. Per aggiungere caselle combinate all'interfaccia utente, creare un elemento [combos](../../extensibility/combos-element.md) nell'elemento `Commands`. Aggiungere quindi all'elemento `Combos` un elemento `Combo` per ogni casella combinata da aggiungere. gli elementi `Combo` hanno gli stessi attributi e figli degli elementi `Button` e hanno anche attributi di `DefaultWidth` e `idCommandList`. L'attributo `DefaultWidth` imposta la larghezza in pixel e l'attributo `idCommandList` punta a un ID di comando utilizzato per popolare la casella combinata.

   - Controller menu: un controller di menu è un pulsante con una freccia accanto. Facendo clic sulla freccia si apre un elenco. Per aggiungere un controller di menu all'interfaccia utente, creare un elemento `Menu` e impostare il relativo attributo `type` su `MenuController` o `MenuControllerLatched`, a seconda del comportamento desiderato. Per popolare un controller di menu, impostarlo come elemento padre di un elemento `Group`. Il controller di menu visualizzerà tutti gli elementi figlio del gruppo nell'elenco a discesa.

## <a name="see-also"></a>Vedere anche
- [Estendi menu e comandi](../../extensibility/extending-menus-and-commands.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimento XML Schema VSCT](../../extensibility/vsct-xml-schema-reference.md)