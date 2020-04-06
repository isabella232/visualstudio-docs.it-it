---
title: Creazione. File di Vsct Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709993"
---
# <a name="author-vsct-files"></a>Creare file vsct
In questo documento viene illustrato come creare un file *vsct* per aggiungere voci di menu, barre degli strumenti e altri elementi dell'interfaccia utente all'ambiente di sviluppo integrato (IDE) di Visual Studio. Utilizzare questi passaggi quando si aggiungono elementi dell'interfaccia utente a un pacchetto di Visual Studio (VSPackage) che non dispone già di un file *con estensione vsct.*

 Per i nuovi progetti, è consigliabile usare il modello di pacchetto di Visual Studio perché genera un file *con estensione vsct* che, a seconda delle selezioni, contiene già gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato. È possibile modificare questo file vsct per soddisfare i requisiti del pacchetto VSPackage.You can modify this *.vsct* file to meet the requirements of your VSPackage. Per ulteriori informazioni su come modificare un file *vsct,* vedere gli esempi in [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Creare il file
 Creare un file *con estensione vsct* in queste fasi: creare la struttura per file e risorse, dichiarare gli elementi dell'interfaccia utente, inserire gli elementi dell'interfaccia utente nell'IDE e aggiungere eventuali comportamenti specializzati.

### <a name="file-structure"></a>Struttura dei file
 La struttura di base di un file *vsct* è un [CommandTable](../../extensibility/commandtable-element.md) elemento radice che contiene un [Commands](../../extensibility/commands-element.md) elemento e un [Symbols](../../extensibility/symbols-element.md) elemento.

#### <a name="to-create-the-file-structure"></a>Per creare la struttura di file

1. Aggiungere un file *con estensione vsct* al progetto seguendo la procedura descritta in [Procedura: creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Aggiungere gli spazi dei `CommandTable` nomi necessari all'elemento, come illustrato nell'esempio seguente:Add the required namespaces to the element, as shown in the following example:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Nell'elemento `CommandTable` aggiungere `Commands` un elemento per ospitare tutti i menu, le barre degli strumenti, i gruppi di comandi e i comandi personalizzati. Per poter caricare gli elementi `Commands` dell'interfaccia `Package` utente personalizzati, l'elemento deve avere il relativo attributo impostato sul nome del pacchetto.

     Dopo `Commands` l'elemento, `Symbols` aggiungere un elemento per definire i GUID per il pacchetto e i nomi e gli ID di comando per gli elementi dell'interfaccia utente.

### <a name="include-visual-studio-resources"></a>Includi risorse di Visual Studio
 Usare l'elemento [Extern](../../extensibility/extern-element.md) per accedere ai file che definiscono i comandi di Visual Studio e ai menu necessari per inserire gli elementi dell'interfaccia utente nell'IDE. Se si utilizzeranno comandi definiti all'esterno del pacchetto, usare l'elemento UsedCommands per informare Visual Studio.If you will use commands defined outside your package, use the [UsedCommands](../../extensibility/usedcommands-element.md) element to inform Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Per includere le risorse di Visual StudioTo include Visual Studio resources

1. All'inizio dell'elemento `CommandTable` aggiungere `Extern` un elemento per ogni file esterno `href` a cui fare riferimento e impostare l'attributo sul nome del file. È possibile fare riferimento ai file di intestazione seguenti per accedere alle risorse di Visual Studio:You can reference the following header files to access Visual Studio resources:

   - *Stdidcmd.h*: Definisce gli ID per tutti i comandi esposti da Visual Studio.Stdidcmd.h : Defines IDs for all commands exposed by Visual Studio.

   - *Vsshlids.h*: contiene gli ID di comando per i menu di Visual Studio.

2. Se il pacchetto chiama i comandi definiti da Visual Studio `UsedCommands` o `Commands` da altri pacchetti, aggiungere un elemento dopo l'elemento. Popolare questo elemento con un [UsedCommand](../../extensibility/usedcommand-element.md) elemento per ogni comando chiamato che non fa parte del pacchetto. Impostare `guid` `id` gli attributi `UsedCommand` e degli elementi sui valori GUID e ID dei comandi da chiamare.

   Per ulteriori informazioni su come trovare i GUID e gli ID dei comandi di Visual Studio, vedere [GUID e ID dei comandi di Visual Studio.](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md) Per chiamare comandi da altri pacchetti, usare il GUID e l'ID del comando come definito nel file *vsct* per tali pacchetti.

### <a name="declare-ui-elements"></a>Dichiarare gli elementi dell'interfaccia utenteDeclare UI elements
 Dichiarare tutti i nuovi `Symbols` elementi dell'interfaccia utente nella sezione del file *vsct.*

#### <a name="to-declare-ui-elements"></a>Per dichiarare gli elementi dell'interfaccia utenteTo declare UI elements

1. Nell'elemento aggiungere tre elementi `Symbols` [GuidSymbol.In](../../extensibility/guidsymbol-element.md) the element, add three GuidSymbol elements. Ogni `GuidSymbol` elemento `name` ha un `value` attributo e un attributo. Impostare `name` l'attributo in modo che rifletta lo scopo dell'elemento. L'attributo `value` accetta un GUID. Per generare un GUID, scegliere **Crea GUID**dal menu **Strumenti** , quindi **Formato Registro**di sistema .

     Il `GuidSymbol` primo elemento rappresenta il pacchetto e in genere non ha elementi figlio. Il `GuidSymbol` secondo elemento rappresenta il set di comandi e conterrà tutti i simboli che definiscono i menu, i gruppi e i comandi. Il `GuidSymbol` terzo elemento rappresenta l'archivio immagini e contiene simboli per tutte le icone per i comandi. Se non sono presenti comandi che utilizzano icone, è possibile omettere il terzo `GuidSymbol` elemento.

2. Nell'elemento `GuidSymbol` che rappresenta il set di comandi aggiungere uno o più elementi [IDSymbol.](../../extensibility/idsymbol-element.md) Ognuna di queste rappresenta un menu, una barra degli strumenti, un gruppo o un comando che si sta aggiungendo all'interfaccia utente.

     Per `IDSymbol` ogni elemento, `name` impostare l'attributo sul nome che verrà utilizzato per fare `value` riferimento al menu, al gruppo o al comando corrispondente, quindi impostare l'elemento su un numero esadecimale che rappresenterà il relativo ID di comando. Due `IDSymbol` elementi che hanno lo stesso elemento padre non possono avere lo stesso valore.

3. Se uno degli elementi dell'interfaccia `IDSymbol` utente richiede icone, `GuidSymbol` aggiungi un elemento per ogni icona all'elemento che rappresenta l'archivio immagini.

### <a name="put-ui-elements-in-the-ide"></a>Inserire elementi dell'interfaccia utente nell'IDE
 Gli elementi [Menus](../../extensibility/menus-element.md), [Groups](../../extensibility/groups-element.md)e [Buttons](../../extensibility/buttons-element.md) contengono le definizioni per tutti i menu, i gruppi e i comandi definiti nel pacchetto. Inserire questi menu, gruppi e comandi nell'IDE usando un elemento [Parent,](../../extensibility/parent-element.md) che fa parte della definizione dell'elemento dell'interfaccia utente, o usando un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) definito altrove.

 Ogni `Menu` `Group`elemento `Button` , , `guid` e `id` dispone di un attributo e di un attributo . Impostare `guid` sempre l'attributo `GuidSymbol` in modo che corrisponda al `id` nome dell'elemento `IDSymbol` che rappresenta il set di comandi `Symbols` e impostare l'attributo sul nome dell'elemento che rappresenta il menu, il gruppo o il comando nella sezione.

#### <a name="to-define-ui-elements"></a>Per definire gli elementi dell'interfaccia utenteTo define UI elements

1. Se si definiscono nuovi menu, sottomenu, menu di scelta rapida `Menus` o `Commands` barre degli strumenti, aggiungere un elemento all'elemento. Quindi, per ogni menu da [Menu](../../extensibility/menu-element.md) creare, aggiungere `Menus` un Menu elemento all'elemento.

    Impostare `guid` `id` gli attributi `Menu` e dell'elemento, quindi impostare l'attributo `type` sul tipo di menu desiderato. È inoltre possibile `priority` impostare l'attributo per stabilire la posizione relativa del menu nel gruppo padre.

   > [!NOTE]
   > L'attributo `priority` non si applica alle barre degli strumenti e ai menu di scelta rapida.

2. Tutti i comandi nell'IDE di Visual Studio devono essere ospitati da gruppi di comandi, che sono gli elementi figlio diretti di menu e barre degli strumenti. Se si aggiungono nuovi menu o barre degli strumenti all'IDE, questi devono contenere nuovi gruppi di comandi. È inoltre possibile aggiungere gruppi di comandi ai menu e alle barre degli strumenti esistenti in modo da poter raggruppare visivamente i comandi.

    Quando si aggiungono nuovi gruppi di `Groups` comandi, è necessario innanzitutto creare un elemento e quindi aggiungervi un elemento [Group](../../extensibility/group-element.md) per ogni gruppo di comandi.

    Impostare `guid` `id` gli attributi `Group` e di ogni `priority` elemento, quindi impostare l'attributo per stabilire la posizione relativa del gruppo nel menu padre. Per ulteriori informazioni, consultate [Creare gruppi riutilizzabili di pulsanti.](../../extensibility/creating-reusable-groups-of-buttons.md)

3. Se si aggiungono nuovi comandi all'IDE, aggiungere un `Buttons` elemento all'elemento. `Commands` Quindi, per ogni comando, aggiungere `Buttons` un [Button](../../extensibility/button-element.md) elemento all'elemento.

   1. Impostare `guid` `id` gli attributi `Button` e di ogni `type` elemento, quindi impostare l'attributo sul tipo di pulsante desiderato. È inoltre possibile `priority` impostare l'attributo per stabilire la posizione relativa del comando nel gruppo padre.

       > [!NOTE]
       > Utilizzare `type="button"` per i comandi di menu e i pulsanti standard sulle barre degli strumenti.

   2. Nell'elemento `Button` aggiungere un elemento [Strings](../../extensibility/strings-element.md) contenente un elemento [ButtonText](../../extensibility/buttontext-element.md) e un elemento [CommandName.](../../extensibility/commandname-element.md) L'elemento `ButtonText` fornisce l'etichetta di testo per una voce di menu o la descrizione comando per un pulsante della barra degli strumenti. L'elemento `CommandName` fornisce il nome del comando da utilizzare nel contenitore dei comandi.

   3. Se il comando avrà un'icona, creare `Button` un [Icon](../../extensibility/icon-element.md) elemento nell'elemento e impostare i relativi `guid` e `id` gli attributi per l'elemento `Bitmap` per l'icona.

       > [!NOTE]
       > I pulsanti della barra degli strumenti devono avere icone.

   Per ulteriori informazioni, vedere [MenuCommands vs.](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)

4. Se uno dei comandi richiede icone, aggiungere `Commands` un [Bitmaps](../../extensibility/bitmaps-element.md) elemento all'elemento. Quindi, per ogni icona, [Bitmap](../../extensibility/bitmap-element.md) aggiungere un `Bitmaps` Bitmap elemento all'elemento. Qui è dove si specifica il percorso della risorsa bitmap. Per ulteriori informazioni, consultate [Aggiungere icone ai comandi di menu.](../../extensibility/adding-icons-to-menu-commands.md)

   È possibile fare affidamento sulla struttura padre per posizionare correttamente la maggior parte dei menu, gruppi e comandi. Per set di comandi molto grandi o quando un menu, un gruppo o un comando deve essere visualizzato in più posizioni, è consigliabile specificare la posizione dei comandi.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>To rely on parenting to place UI elements in the IDE

1. Per l'elemento padre `Parent` tipico, `Menu` `Group`creare `Command` un elemento in ogni elemento , e definito nel pacchetto.

    La destinazione `Parent` dell'elemento è il menu o il gruppo che conterrà il menu, il gruppo o il comando.

   1. Impostare `guid` l'attributo `GuidSymbol` sul nome dell'elemento che definisce il set di comandi. Se l'elemento di destinazione non fa parte del pacchetto, utilizzare il guid per il set di comandi, come definito nel file *vsct* corrispondente.

   2. Impostare `id` l'attributo in modo che corrisponda all'attributo `id` del menu o del gruppo di destinazione. Per un elenco dei menu e dei gruppi esposti da Visual Studio, vedere [GUID e ID di menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) di Visual Studio o GUID e ID delle barre degli strumenti di Visual [Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Se si dispone di un numero elevato di elementi dell'interfaccia utente da inserire nell'IDE o se si dispone di elementi che devono essere visualizzati in più posizioni, definire i posizionamenti nell'elemento [CommandPlacements,](../../extensibility/commandplacements-element.md) come illustrato nei passaggi seguenti.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>To use command placement to place UI elements in the IDE

1. Dopo l'elemento `Commands` aggiungere un elemento `CommandPlacements`.

2. Nell'elemento `CommandPlacements` aggiungere `CommandPlacement` un elemento per ogni menu, gruppo o comando da inserire.

    Ogni `CommandPlacement` elemento `Parent` o elemento inserisce un menu, gruppo o comando in una posizione dell'IDE. Un elemento dell'interfaccia utente può avere un solo elemento padre, ma può avere più posizioni di comando. Per inserire un elemento dell'interfaccia `CommandPlacement` utente in più posizioni, aggiungi un elemento per ogni posizione.

3. Impostare `guid` `id` gli attributi `CommandPlacement` e di ogni elemento sul menu o `Parent` sul gruppo di hosting, come per un elemento. Puoi anche impostare l'attributo `priority` per stabilire la posizione relativa dell'elemento dell'interfaccia utente.

   È possibile combinare il posizionamento in base alla genitorialità e al posizionamento dei comandi. Tuttavia, per set di comandi di grandi dimensioni, è consigliabile utilizzare solo il posizionamento dei comandi.

### <a name="add-specialized-behaviors"></a>Aggiungere comportamenti specializzati
 È possibile utilizzare l'elemento [CommandFlag](../../extensibility/command-flag-element.md) per modificare il comportamento di menu e comandi, ad esempio per modificarne l'aspetto e la visibilità. È inoltre possibile modificare quando un comando è visibile utilizzando il [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) elemento o aggiungere tasti di scelta rapida utilizzando il [KeyBindings](../../extensibility/keybindings-element.md) elemento. Alcuni tipi di menu e comandi hanno già comportamenti specializzati incorporati.

#### <a name="to-add-specialized-behaviors"></a>Per aggiungere comportamenti specializzati

1. Per rendere visibile un elemento dell'interfaccia utente solo in determinati contesti dell'interfaccia utente, ad esempio quando viene caricata una soluzione, usare i vincoli di visibilità.

   1. Dopo l'elemento `Commands` aggiungere un elemento `VisibilityConstraints`.

   2. Per ogni elemento dell'interfaccia utente da vincolare, aggiungere un [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.

   3. Per `VisibilityItem` ogni elemento, `guid` `id` impostare gli attributi e sul menu, `context` il gruppo o il comando, quindi <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> impostare l'attributo sul contesto dell'interfaccia utente desiderato, come definito nella classe.

2. Per impostare la visibilità o la disponibilità di un elemento dell'interfaccia utente nel codice, utilizzare uno o più dei seguenti flag di comando:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Per altre informazioni, vedere l'elemento [CommandFlag.For](../../extensibility/command-flag-element.md) more information, see the CommandFlag element.

3. Per modificare la modalità di visualizzazione di un elemento o modificarne l'aspetto in modo dinamico, utilizzare uno o più dei seguenti flag di comando:

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

   Per altre informazioni, vedere l'elemento [CommandFlag.For](../../extensibility/command-flag-element.md) more information, see the CommandFlag element.

4. Per modificare la modalità di reazione di un elemento quando riceve i comandi, utilizzare uno o più dei seguenti flag di comando:

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

   Per altre informazioni, vedere l'elemento [CommandFlag.For](../../extensibility/command-flag-element.md) more information, see the CommandFlag element.

5. Per associare una scelta rapida da tastiera dipendente dal menu a un menu o a `ButtonText` una voce di un menu, aggiungete un carattere e commerciale (&) nell'elemento per il menu o la voce di menu. Il carattere che segue la e commerciale è il tasto di scelta rapida attivo quando il menu padre è aperto.

6. Per associare un tasto di scelta rapida indipendente dal menu a un comando, utilizzare il [KeyBindings](../../extensibility/keybindings-element.md) elemento. Per altre informazioni, vedere l'elemento [KeyBinding.For](../../extensibility/keybinding-element.md) more information, see the KeyBinding element.

7. Per localizzare il testo `LocCanonicalName` del menu, utilizzare l'elemento . Per altre informazioni, vedere l'elemento [Strings.For](../../extensibility/strings-element.md) more information, see the Strings element.

   Alcuni tipi di menu e pulsanti includono comportamenti specializzati. Nell'elenco seguente vengono descritti alcuni tipi di menu e pulsanti specializzati. Per altri tipi, `types` vedere le descrizioni degli attributi negli elementi [Menu](../../extensibility/menu-element.md), [Button](../../extensibility/button-element.md)e [Combo](../../extensibility/combo-element.md) .

   - Casella combinata: una casella combinata è un elenco a discesa che può essere utilizzato su una barra degli strumenti. Per aggiungere caselle combinate all'interfaccia utente, creare un [Combos](../../extensibility/combos-element.md) elemento nell'elemento. `Commands` Aggiungere quindi `Combos` all'elemento un `Combo` elemento per ogni casella combinata da aggiungere. `Combo`gli elementi hanno gli `Button` stessi attributi `DefaultWidth` e `idCommandList` gli stessi elementi figlio degli elementi e hanno e hanno anche attributi. L'attributo `DefaultWidth` imposta la larghezza `idCommandList` in pixel e punta a un ID di comando utilizzato per popolare la casella combinata.

   - Controller di menu: un controller di menu è un pulsante che contiene una freccia accanto. Facendo clic sulla freccia si apre un elenco. Per aggiungere un controller di menu `Menu` all'interfaccia `type` utente, creare un elemento e impostarne l'attributo su `MenuController` o `MenuControllerLatched`, a seconda del comportamento desiderato. Per popolare un controller di menu, `Group` impostarlo come padre di un elemento. Il controller di menu visualizzerà tutti gli elementi figlio di tale gruppo nel relativo elenco a discesa.

## <a name="see-also"></a>Vedere anche
- [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimento allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
