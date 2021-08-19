---
title: Creazione. Vsct Files | Microsoft Docs
description: Informazioni su come creare file con estensione vsct che aggiungono voci di menu, barre degli strumenti e altri elementi dell'interfaccia utente all'ambiente Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0f28286276bf2616ed84b68caf84949398b3f20e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159295"
---
# <a name="author-vsct-files"></a>Creare file con estensione vsct
Questo documento illustra come creare un file *vsct* per aggiungere voci di menu, barre degli strumenti e altri elementi dell'interfaccia utente all'ambiente di sviluppo integrato (IDE) di Visual Studio. Usare questa procedura quando si aggiungono elementi dell'interfaccia utente a un pacchetto Visual Studio (VSPackage) che non dispone già di un file *vsct.*

 Per i nuovi progetti, è consigliabile usare il modello di pacchetto Visual Studio perché genera un file *vsct* che, a seconda delle selezioni, contiene già gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato. È possibile modificare questo file *con estensione vsct* per soddisfare i requisiti del pacchetto VSPackage. Per altre informazioni su come modificare un file con estensione *vsct,* vedere gli esempi in [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Creare il file
 Creare un file *vsct* in queste fasi: creare la struttura per file e risorse, dichiarare gli elementi dell'interfaccia utente, inserire gli elementi dell'interfaccia utente nell'IDE e aggiungere eventuali comportamenti specializzati.

### <a name="file-structure"></a>Struttura dei file
 La struttura di base di un file *con estensione vsct* è un elemento radice [CommandTable](../../extensibility/commandtable-element.md) che contiene un [elemento Commands](../../extensibility/commands-element.md) e un [elemento Symbols.](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Per creare la struttura di file

1. Aggiungere un file *vsct* al progetto seguendo la procedura descritta in [Procedura: Creare un file vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Aggiungere gli spazi dei nomi necessari `CommandTable` all'elemento , come illustrato nell'esempio seguente:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Nell'elemento aggiungere un elemento per ospitare tutti i menu, le barre degli strumenti, i gruppi di `CommandTable` comandi e i comandi `Commands` personalizzati. In modo che gli elementi dell'interfaccia utente personalizzati possano essere caricati, l'elemento `Commands` deve avere l'attributo impostato sul nome del `Package` pacchetto.

     Dopo l'elemento , aggiungere un elemento per definire i GUID per il pacchetto e i nomi e gli ID di comando `Commands` `Symbols` per gli elementi dell'interfaccia utente.

### <a name="include-visual-studio-resources"></a>Includere Visual Studio risorse
 Usare [l'elemento Extern](../../extensibility/extern-element.md) per accedere ai file che definiscono Visual Studio comandi e ai menu necessari per inserire gli elementi dell'interfaccia utente nell'IDE. Se si useranno comandi definiti all'esterno del pacchetto, usare [l'elemento UsedCommands](../../extensibility/usedcommands-element.md) per Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Per includere Visual Studio risorse

1. Nella parte superiore dell'elemento aggiungere un elemento per ogni file esterno a cui fare riferimento e impostare l'attributo sul `CommandTable` `Extern` nome del `href` file. È possibile fare riferimento ai file di intestazione seguenti per accedere Visual Studio risorse:

   - *Stdidcmd.h:* definisce gli ID per tutti i comandi esposti da Visual Studio.

   - *Vsshlids.h:* contiene gli ID comando per Visual Studio menu.

2. Se il pacchetto chiama i comandi definiti da Visual Studio o da altri pacchetti, aggiungere un `UsedCommands` elemento dopo `Commands` l'elemento . Popolare questo elemento con un [elemento UsedCommand](../../extensibility/usedcommand-element.md) per ogni comando chiamato che non fa parte del pacchetto. Impostare gli attributi e degli elementi nei valori GUID e `guid` ID dei comandi da `id` `UsedCommand` chiamare.

   Per altre informazioni su come trovare i GUID e gli ID dei comandi Visual Studio, vedere GUID e ID dei Visual Studio [comandi](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Per chiamare comandi da altri pacchetti, usare il GUID e l'ID del comando come definito nel file *vsct* per tali pacchetti.

### <a name="declare-ui-elements"></a>Dichiarare elementi dell'interfaccia utente
 Dichiarare tutti i nuovi elementi dell'interfaccia utente `Symbols` nella sezione del file con estensione *vsct.*

#### <a name="to-declare-ui-elements"></a>Per dichiarare gli elementi dell'interfaccia utente

1. `Symbols`Nell'elemento aggiungere tre elementi [GuidSymbol.](../../extensibility/guidsymbol-element.md) Ogni `GuidSymbol` elemento ha un attributo e un attributo `name` `value` . Impostare `name` l'attributo in modo che rifletta lo scopo dell'elemento . `value`L'attributo accetta un GUID. Per generare un GUID, scegliere Crea **GUID** dal **menu** Strumenti e quindi Formato Registro **di sistema.**

     Il primo `GuidSymbol` elemento rappresenta il pacchetto e in genere non ha elementi figlio. Il secondo elemento rappresenta il set di comandi e conterrà tutti i simboli che definiscono `GuidSymbol` menu, gruppi e comandi. Il terzo `GuidSymbol` elemento rappresenta l'archivio immagini e contiene simboli per tutte le icone per i comandi. Se non sono disponibili comandi che usano icone, è possibile omettere il terzo `GuidSymbol` elemento.

2. `GuidSymbol`Nell'elemento che rappresenta il set di comandi aggiungere uno o più elementi [IDSymbol.](../../extensibility/idsymbol-element.md) Ognuna di queste rappresenta un menu, una barra degli strumenti, un gruppo o un comando da aggiungere all'interfaccia utente.

     Per ogni elemento, impostare l'attributo sul nome che verrà utilizzato per fare riferimento al menu, al gruppo o al comando corrispondente e quindi impostare l'elemento su un numero esadecimale che rappresenta `IDSymbol` `name` l'ID `value` comando. Due elementi `IDSymbol` che hanno lo stesso elemento padre non possono avere lo stesso valore.

3. Se uno degli elementi dell'interfaccia utente richiede icone, aggiungere un elemento `IDSymbol` per ogni icona all'elemento che rappresenta `GuidSymbol` l'archivio immagini.

### <a name="put-ui-elements-in-the-ide"></a>Inserire elementi dell'interfaccia utente nell'IDE
 Gli [elementi Menu,](../../extensibility/menus-element.md) [Gruppi](../../extensibility/groups-element.md)e [Pulsanti](../../extensibility/buttons-element.md) contengono le definizioni per tutti i menu, i gruppi e i comandi definiti nel pacchetto. Inserire questi menu, gruppi e comandi nell'IDE usando un elemento [Parent,](../../extensibility/parent-element.md) che fa parte della definizione dell'elemento ui, o usando un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) definito altrove.

 Ogni `Menu` elemento , e ha un attributo e un attributo `Group` `Button` `guid` `id` . Impostare sempre l'attributo in modo che corrisponda al nome dell'elemento che rappresenta il set di comandi e impostare l'attributo sul nome dell'elemento che rappresenta il menu, il gruppo o il comando `guid` `GuidSymbol` nella sezione `id` `IDSymbol` `Symbols` .

#### <a name="to-define-ui-elements"></a>Per definire gli elementi dell'interfaccia utente

1. Se si definiscono nuovi menu, sottomenu, menu di scelta rapida o barre degli strumenti, aggiungere un `Menus` elemento `Commands` all'elemento . Quindi, per ogni menu da creare, aggiungere un [elemento Menu](../../extensibility/menu-element.md) all'elemento `Menus` .

    Impostare gli `guid` attributi `id` e `Menu` dell'elemento e quindi impostare `type` l'attributo sul tipo di menu desiderato. È anche possibile impostare `priority` l'attributo per stabilire la posizione relativa del menu nel gruppo padre.

   > [!NOTE]
   > `priority`L'attributo non si applica alle barre degli strumenti e ai menu di scelta rapida.

2. Tutti i comandi nell Visual Studio IDE devono essere ospitati da gruppi di comandi, che sono gli elementi figlio diretti di menu e barre degli strumenti. Se si aggiungono nuovi menu o barre degli strumenti all'IDE, questi devono contenere nuovi gruppi di comandi. È anche possibile aggiungere gruppi di comandi a menu e barre degli strumenti esistenti in modo da poter raggruppare visivamente i comandi.

    Quando si aggiungono nuovi gruppi di comandi, è prima necessario creare un elemento e quindi aggiungervi un `Groups` [elemento Group](../../extensibility/group-element.md) per ogni gruppo di comandi.

    Impostare gli attributi e di ogni elemento e quindi impostare l'attributo per stabilire la posizione relativa del `guid` `id` gruppo nel menu `Group` `priority` padre. Per altre informazioni, vedere [Creare gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Se si aggiungono nuovi comandi all'IDE, aggiungere un `Buttons` elemento `Commands` all'elemento . Quindi, per ogni comando, aggiungere un [elemento Button](../../extensibility/button-element.md) all'elemento `Buttons` .

   1. Impostare gli `guid` attributi e di ogni elemento e quindi impostare `id` l'attributo sul tipo di pulsante `Button` `type` desiderato. È anche possibile impostare `priority` l'attributo per stabilire la posizione relativa del comando nel gruppo padre.

       > [!NOTE]
       > Usare `type="button"` per i comandi di menu e i pulsanti standard sulle barre degli strumenti.

   2. `Button`Nell'elemento aggiungere un elemento [Strings](../../extensibility/strings-element.md) contenente un [elemento ButtonText](../../extensibility/buttontext-element.md) e un [elemento CommandName.](../../extensibility/commandname-element.md) `ButtonText`L'elemento fornisce l'etichetta di testo per una voce di menu o la descrizione comando per un pulsante della barra degli strumenti. `CommandName`L'elemento fornisce il nome del comando da usare nell'oggetto comando.

   3. Se il comando avrà un'icona, creare un [elemento Icon](../../extensibility/icon-element.md) nell'elemento e impostarne gli attributi `Button` e `guid` `id` `Bitmap` sull'elemento per l'icona.

       > [!NOTE]
       > I pulsanti della barra degli strumenti devono avere icone.

   Per altre informazioni, vedere [MenuCommands e OleMenuCommands.](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)

4. Se uno dei comandi richiede icone, aggiungere un [elemento Bitmaps](../../extensibility/bitmaps-element.md) all'elemento `Commands` . Quindi, per ogni icona, aggiungere un [elemento Bitmap](../../extensibility/bitmap-element.md) all'elemento `Bitmaps` . Qui è possibile specificare il percorso della risorsa bitmap. Per altre informazioni, vedere [Aggiungere icone ai comandi di menu.](../../extensibility/adding-icons-to-menu-commands.md)

   È possibile fare affidamento sulla struttura padre per posizionare correttamente la maggior parte dei menu, dei gruppi e dei comandi. Per set di comandi di grandi dimensioni o quando un menu, un gruppo o un comando deve essere visualizzato in più posizioni, è consigliabile specificare la posizione dei comandi.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Per basarsi sull'elemento padre per posizionare gli elementi dell'interfaccia utente nell'IDE

1. Per l'elemento padre tipico, `Parent` creare un elemento in ogni elemento , e definito nel `Menu` `Group` `Command` pacchetto.

    La destinazione `Parent` dell'elemento è il menu o il gruppo che conterrà il menu, il gruppo o il comando.

   1. Impostare `guid` l'attributo sul nome `GuidSymbol` dell'elemento che definisce il set di comandi. Se l'elemento di destinazione non fa parte del pacchetto, usare il GUID per il set di comandi, come definito nel file *con estensione vsct* corrispondente.

   2. Impostare `id` l'attributo in modo che `id` corrisponda all'attributo del menu o del gruppo di destinazione. Per un elenco dei menu e dei gruppi esposti da Visual Studio, vedere GUID e ID di [menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) Visual Studio o [GUID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e ID delle barre degli strumenti Visual Studio .

   Se si dispone di un numero elevato di elementi dell'interfaccia utente da inserire nell'IDE o se sono presenti elementi che devono essere visualizzati in più posizioni, definirne le posizioni nell'elemento [CommandPlacements,](../../extensibility/commandplacements-element.md) come illustrato nei passaggi seguenti.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Per usare il posizionamento dei comandi per posizionare gli elementi dell'interfaccia utente nell'IDE

1. Dopo l'elemento `Commands` aggiungere un elemento `CommandPlacements`.

2. `CommandPlacements`Nell'elemento aggiungere un elemento per ogni `CommandPlacement` menu, gruppo o comando da inserire.

    Ogni `CommandPlacement` elemento o elemento `Parent` inserisce un menu, un gruppo o un comando in una posizione IDE. Un elemento dell'interfaccia utente può avere un solo elemento padre, ma può avere più posizionamenti di comandi. Per posizionare un elemento dell'interfaccia utente in più posizioni, aggiungere un `CommandPlacement` elemento per ogni posizione.

3. Impostare gli attributi e di ogni elemento sul menu o sul gruppo di hosting, esattamente `guid` come si farebbe per un `id` `CommandPlacement` `Parent` elemento. È anche possibile impostare `priority` l'attributo per stabilire la posizione relativa dell'elemento dell'interfaccia utente.

   È possibile combinare la posizione padre e il posizionamento dei comandi. Tuttavia, per i set di comandi di grandi dimensioni, è consigliabile usare solo il posizionamento dei comandi.

### <a name="add-specialized-behaviors"></a>Aggiungere comportamenti specializzati
 È possibile usare [l'elemento CommandFlag](../../extensibility/command-flag-element.md) per modificare il comportamento di menu e comandi, ad esempio per modificarne l'aspetto e la visibilità. È anche possibile influire su quando un comando è visibile usando l'elemento [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) o aggiungere tasti di scelta rapida usando [l'elemento KeyBindings.](../../extensibility/keybindings-element.md) Alcuni tipi di menu e comandi hanno già comportamenti specializzati incorporati.

#### <a name="to-add-specialized-behaviors"></a>Per aggiungere comportamenti specializzati

1. Per rendere visibile un elemento dell'interfaccia utente solo in determinati contesti dell'interfaccia utente, ad esempio quando viene caricata una soluzione, usare i vincoli di visibilità.

   1. Dopo l'elemento `Commands` aggiungere un elemento `VisibilityConstraints`.

   2. Per ogni elemento dell'interfaccia utente da vincolare, aggiungere un [elemento VisibilityItem.](../../extensibility/visibilityitem-element.md)

   3. Per ogni elemento, impostare gli attributi e sul menu, sul gruppo o sul comando e quindi impostare l'attributo sul contesto dell'interfaccia utente `VisibilityItem` `guid` `id` `context` desiderato, come definito nella <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classe .

2. Per impostare la visibilità o la disponibilità di un elemento dell'interfaccia utente nel codice, usare uno o più dei flag di comando seguenti:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Per altre informazioni, vedere [l'elemento CommandFlag.](../../extensibility/command-flag-element.md)

3. Per modificare l'aspetto di un elemento o modificarne l'aspetto in modo dinamico, usare uno o più dei flag di comando seguenti:

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

   Per altre informazioni, vedere [l'elemento CommandFlag.](../../extensibility/command-flag-element.md)

4. Per modificare la reazione di un elemento quando riceve comandi, usare uno o più dei flag di comando seguenti:

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

   Per altre informazioni, vedere [l'elemento CommandFlag.](../../extensibility/command-flag-element.md)

5. Per associare un tasto di scelta rapida dipendente dal menu a un menu o a una voce di un menu, aggiungere un carattere e commerciale (&) nell'elemento per il menu o la voce `ButtonText` di menu. Il carattere che segue la e commerciale è il tasto di scelta rapida attivo quando il menu padre è aperto.

6. Per associare un tasto di scelta rapida indipendente dal menu a un comando, usare [l'elemento KeyBindings.](../../extensibility/keybindings-element.md) Per altre informazioni, vedere [l'elemento KeyBinding.](../../extensibility/keybinding-element.md)

7. Per localizzare il testo del menu, usare `LocCanonicalName` l'elemento . Per altre informazioni, vedere [l'elemento Strings.](../../extensibility/strings-element.md)

   Alcuni tipi di menu e pulsanti includono comportamenti specializzati. L'elenco seguente descrive alcuni tipi di menu e pulsanti specializzati. Per altri tipi, vedere le `types` descrizioni degli attributi negli elementi [Menu](../../extensibility/menu-element.md), [Button](../../extensibility/button-element.md)e [Combo.](../../extensibility/combo-element.md)

   - Casella combinata: una casella combinata è un elenco a discesa che può essere utilizzato su una barra degli strumenti. Per aggiungere caselle combinate all'interfaccia utente, creare un [elemento Combos](../../extensibility/combos-element.md) nell'elemento `Commands` . Aggiungere quindi `Combos` all'elemento un `Combo` elemento per ogni casella combinata da aggiungere. `Combo` gli elementi hanno gli stessi attributi e gli stessi elementi figlio `Button` degli elementi e hanno anche gli attributi e `DefaultWidth` `idCommandList` . L'attributo imposta la larghezza in pixel e l'attributo punta a un ID comando usato `DefaultWidth` per popolare la casella `idCommandList` combinata.

   - Controller di menu: un controller di menu è un pulsante con una freccia accanto. Facendo clic sulla freccia viene aperto un elenco. Per aggiungere un controller di menu all'interfaccia utente, creare un elemento e impostarne l'attributo su o , a seconda `Menu` `type` del comportamento `MenuController` `MenuControllerLatched` desiderato. Per popolare un controller di menu, impostarlo come padre di un `Group` elemento. Il controller di menu visualizza tutti gli elementi figlio del gruppo nell'elenco a discesa.

## <a name="see-also"></a>Vedi anche
- [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md)
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Informazioni di riferimento sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)