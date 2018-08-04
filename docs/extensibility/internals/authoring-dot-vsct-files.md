---
title: Creazione. File Vsct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b03c36fdec85c638e708a4f7c99cedd870cc2a71
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498811"
---
# <a name="author-vsct-files"></a>File con estensione vsct autore
Questo documento illustra come creare un *vsct* file per aggiungere voci di menu, barre degli strumenti e altri elementi dell'interfaccia utente per l'ambiente di sviluppo integrato (IDE) di Visual Studio. Usare questi passaggi quando si aggiungono elementi dell'interfaccia utente a un pacchetto di Visual Studio (VSPackage di) che non dispone già di un *vsct* file.  
  
 Per i nuovi progetti, è consigliabile usare il modello di pacchetto di Visual Studio in quanto genera una *vsct* file, a seconda delle selezioni, già con gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato . È possibile modificare questa *vsct* file per soddisfare i requisiti del pacchetto VSPackage. Per altre informazioni su come modificare un *vsct* del file, vedere gli esempi inclusi in [estendono i menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="author-the-file"></a>Creare il file  
 Creare un *con estensione vsct* file in tali fasi: creazione della struttura di file e le risorse, dichiarare gli elementi dell'interfaccia utente, inserire gli elementi dell'interfaccia utente nell'IDE e aggiungere eventuali comportamenti specializzati.  
  
### <a name="file-structure"></a>Struttura di file  
 La struttura di base di un *vsct* file è un [CommandTable](../../extensibility/commandtable-element.md) elemento radice che contiene una [comandi](../../extensibility/commands-element.md) elemento e un [simboli](../../extensibility/symbols-element.md) elemento.  
  
#### <a name="to-create-the-file-structure"></a>Per creare la struttura di file  
  
1.  Aggiungere un *vsct* file al progetto seguendo i passaggi descritti in [procedura: creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2. Aggiungere gli spazi dei nomi necessari per il `CommandTable` elemento, come illustrato nell'esempio seguente:  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  Nel `CommandTable` elemento, aggiungere un `Commands` elemento per ospitare tutti i menu personalizzati, le barre degli strumenti, gruppi di comandi e i comandi. In modo che sia possano caricare gli elementi dell'interfaccia utente personalizzati, il `Commands` l'elemento deve avere il `Package` attributo impostato sul nome del pacchetto.  
  
     Dopo il `Commands` elemento, aggiungere un `Symbols` elemento per definire i GUID per il pacchetto e i nomi e ID di comando per gli elementi dell'interfaccia utente.  
  
### <a name="include-visual-studio-resources"></a>Includere le risorse di Visual Studio  
 Usare la [Extern](../../extensibility/extern-element.md) elemento accedere ai file che definiscono i comandi di Visual Studio e i menu necessari per inserire elementi dell'interfaccia utente nell'IDE. Se si usano comandi definiti all'esterno del pacchetto, usare il [UsedCommands](../../extensibility/usedcommands-element.md) elemento per indicare a Visual Studio.  
  
#### <a name="to-include-visual-studio-resources"></a>Per includere risorse di Visual Studio  
  
1.  Nella parte superiore del `CommandTable` elemento, aggiungerne uno `Extern` (elemento) per ogni file esterno da cui viene fatto riferimento e impostare il `href` attributo sul nome del file. È possibile fare riferimento a file di intestazione seguenti per accedere alle risorse di Visual Studio:  
  
    -   *Stdidcmd.h*: definisce gli ID per tutti i comandi esposti da Visual Studio.  
  
    -   *Vsshlids.h*: contiene gli ID di comando per i menu di Visual Studio.  
  
2.  Se il pacchetto chiama i comandi che sono definiti da Visual Studio o da altri pacchetti, aggiungere un `UsedCommands` elemento dopo il `Commands` elemento. Popolare questo elemento con un [UsedCommand](../../extensibility/usedcommand-element.md) (elemento) per ogni comando è chiamare vale a dire non fa parte del pacchetto. Impostare il `guid` e `id` attributi del `UsedCommand` elementi sui valori GUID e ID dei comandi chiamare. 

   Per altre informazioni su come individuare i comandi i GUID e ID di Visual Studio, vedere [comandi GUID e ID di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Per chiamare i comandi da altri pacchetti, usare il GUID e l'ID del comando come definito nel *vsct* file per tali pacchetti.
  
### <a name="declare-ui-elements"></a>Dichiarare gli elementi dell'interfaccia utente  
 Dichiarare tutti i nuovi elementi dell'interfaccia utente nel `Symbols` sezione il *vsct* file.  
  
#### <a name="to-declare-ui-elements"></a>Per dichiarare gli elementi dell'interfaccia utente  
  
1.  Nel `Symbols` elemento, aggiungere tre [GuidSymbol](../../extensibility/guidsymbol-element.md) elementi. Ciascuna `GuidSymbol` elemento ha un `name` attributo e un `value` attributo. Impostare il `name` attributo in modo da riflettere lo scopo dell'elemento. Il `value` attributo accetta un GUID. (Per generare un GUID, nella **degli strumenti** dal menu **Crea GUID**e quindi selezionare **formato del Registro di sistema**.)  
  
     Il primo `GuidSymbol` elemento rappresenta il pacchetto e in genere non ha elementi figlio. Il secondo `GuidSymbol` element rappresenta il comando set e conterrà tutti i simboli che definiscono i menu, gruppi e i comandi. Il terzo `GuidSymbol` elemento rappresenta l'archivio di immagini e contiene i simboli per tutte le icone per i comandi. Se non si dispone di alcun comando che usano le icone, è possibile omettere il terzo `GuidSymbol` elemento.  
  
2.  Nel `GuidSymbol` elemento che rappresenta il set di comandi, aggiungere uno o più [IDSymbol](../../extensibility/idsymbol-element.md) elementi. Ciascuno di questi rappresenta un menu, barra degli strumenti, gruppo o comando per aggiungere l'interfaccia utente.  
  
     Per ognuno `IDSymbol` elemento, impostare il `name` dell'attributo al nome verrà usato per fare riferimento al menu corrispondente, gruppo o comando e quindi impostare il `value` elemento in un numero esadecimale che rappresenta l'ID di comando. Nessuna due `IDSymbol` gli elementi aventi lo stesso elemento padre possono avere lo stesso valore.  
  
3.  Se uno qualsiasi degli elementi dell'interfaccia utente richiede le icone, aggiungere un' `IDSymbol` (elemento) per ogni icona per il `GuidSymbol` elemento che rappresenta l'archivio immagini.  
  
### <a name="put-ui-elements-in-the-ide"></a>Inserire gli elementi dell'interfaccia utente nell'IDE  
 Il [menu di scelta](../../extensibility/menus-element.md), [gruppi](../../extensibility/groups-element.md), e [pulsanti](../../extensibility/buttons-element.md) elementi contengono le definizioni per tutti i menu, gruppi e i comandi che sono definiti nel pacchetto. Inserire questi menu, gruppi e i comandi nell'IDE tramite un [padre](../../extensibility/parent-element.md) elemento, che fa parte della definizione dell'elemento dell'interfaccia utente o con un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento che viene definito altrove.  
  
 Ciascuna `Menu`, `Group`, e `Button` elemento dispone di una `guid` attributo e un `id` attributo. Sempre impostato il `guid` attributo corrisponda al nome del `GuidSymbol` elemento che rappresenta il comando set e impostare il `id` attributo sul nome del `IDSymbol` elemento che rappresenta il menu, gruppo o comando per il `Symbols`sezione.  
  
#### <a name="to-define-ui-elements"></a>Per definire gli elementi dell'interfaccia utente  
  
1.  Se si sta definendo eventuali nuovi menu, sottomenu, menu di scelta rapida o le barre degli strumenti, aggiungere un `Menus` elemento per il `Commands` elemento. Quindi, per ogni menu deve essere creato, aggiungere un [dal Menu](../../extensibility/menu-element.md) elemento per il `Menus` elemento.  
  
     Impostare il `guid` e `id` attributi del `Menu` elemento e quindi impostare il `type` attributo al tipo di menu che si desidera. È anche possibile impostare il `priority` attributo per stabilire la posizione relativa del menu del gruppo padre.  
  
    > [!NOTE]
    >  Il `priority` attributo non è applicabile per le barre degli strumenti e menu di scelta rapida.  
  
2.  Tutti i comandi nell'IDE di Visual Studio devono essere ospitati da gruppi di comandi che sono figli diretti del menu e barre degli strumenti. Se si aggiunge nuovi menu o barre degli strumenti all'IDE, questi devono contenere nuovi gruppi di comandi. È anche possibile aggiungere gruppi di comandi a menu e barre degli strumenti esistenti in modo che è possibile raggruppare in modo visivo i comandi.  
  
     Quando si aggiungono nuovi gruppi di comandi, è innanzitutto necessario creare un `Groups` elemento e quindi aggiungervi un [gruppo](../../extensibility/group-element.md) (elemento) per ogni gruppo di comandi.  
  
     Impostare il `guid` e `id` attributi della ognuno `Group` elemento e quindi impostare il `priority` attributo per stabilire la posizione relativa del gruppo nel menu del padre. Per altre informazioni, vedere [creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Se si aggiungono nuovi comandi all'IDE, aggiungere un `Buttons` elemento per il `Commands` elemento. Quindi, per ogni comando, aggiungere un [sul pulsante](../../extensibility/button-element.md) elemento per il `Buttons` elemento.  
  
    1.  Impostare il `guid` e `id` gli attributi della ognuno `Button` elemento e quindi impostare il `type` attributo al tipo di pulsante desiderato. È anche possibile impostare il `priority` attributo per stabilire la posizione relativa del comando del gruppo padre.  
  
        > [!NOTE]
        >  Usare `type="button"` per i comandi di menu standard e i pulsanti sulle barre degli strumenti.  
  
    2.  Nel `Button` elemento, aggiungere un [stringhe](../../extensibility/strings-element.md) elemento contenente una [ButtonText](../../extensibility/buttontext-element.md) elemento e una [CommandName](../../extensibility/commandname-element.md) elemento. Il `ButtonText` elemento fornisce l'etichetta di testo per una voce di menu o la descrizione comando per un pulsante della barra degli strumenti. Il `CommandName` elemento fornisce il nome del comando da usare anche nel comando.  
  
    3.  Se il comando avrà un'icona, creare un [icona](../../extensibility/icon-element.md) elemento il `Button` e impostare relativo `guid` e `id` attributi per il `Bitmap` (elemento) per l'icona.  
  
        > [!NOTE]
        >  I pulsanti della barra degli strumenti devono avere le icone.  
  
   Per altre informazioni, vedere [vs confronto tra oggetti MenuCommand. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4.  Se uno qualsiasi dei comandi richiedono le icone, aggiungere un [bitmap](../../extensibility/bitmaps-element.md) elemento per il `Commands` elemento. Quindi, per ogni icona, aggiungere un [Bitmap](../../extensibility/bitmap-element.md) elemento per il `Bitmaps` elemento. Si tratta in cui si specificherà il percorso della risorsa bitmap. Per altre informazioni, vedere [aggiungere le icone ai comandi di menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
 È possibile basarsi sulla struttura genitorialità posizionare correttamente la maggior parte dei menu, gruppi e i comandi. Per i set di comandi di dimensioni molto grandi, o quando un menu, gruppo o comando deve apparire in più posizioni, è consigliabile specificare commandplacement.  
  
#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Affidarsi a elemento padre di posizionare gli elementi dell'interfaccia utente nell'IDE  
  
1.  Per la tipica genitorialità, creare un `Parent` ogni elemento `Menu`, `Group`, e `Command` elemento definito nel pacchetto.  
  
     La destinazione del `Parent` elemento è il menu di scelta o gruppo che contiene i menu, gruppo o comando.  
  
    1.  Impostare il `guid` dell'attributo sul nome del `GuidSymbol` elemento che definisce il set di comandi. Se l'elemento di destinazione non fa parte del pacchetto, usare il guid per il set di comandi, come definito nel corrispondente *vsct* file.  
  
    2.  Impostare il `id` attributo in modo che corrisponda il `id` attributo del menu di destinazione o del gruppo. Per un elenco dei menu e i gruppi che vengono esposte da Visual Studio, vedere [menu GUID e ID di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oppure [GUID e ID di Visual Studio le barre degli strumenti](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Se si dispone di un numero elevato di elementi dell'interfaccia utente da inserire nell'IDE, o se si dispongono di elementi che devono apparire in più posizioni, definire le posizioni nel [CommandPlacements](../../extensibility/commandplacements-element.md) elemento, come illustrato nei passaggi seguenti.  
  
#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Per usare il posizionamento di comando di posizionare gli elementi dell'interfaccia utente nell'IDE  
  
1.  Dopo il `Commands` elemento, aggiungere un `CommandPlacements` elemento.  
  
2.  Nel `CommandPlacements` elemento, aggiungere un `CommandPlacement` (elemento) per ogni menu, gruppo o comando da inserire.  
  
     Ciascuna `CommandPlacement` elemento o `Parent` elemento inserisce un menu, gruppo o comando in un'unica posizione IDE. Un elemento dell'interfaccia utente può avere un solo padre, ma può avere più elementi commandplacement. Per inserire un elemento dell'interfaccia utente in più percorsi, aggiungere un `CommandPlacement` (elemento) per ogni posizione.  
  
3.  Impostare il `guid` e `id` attributi della ognuno `CommandPlacement` elemento per l'hosting menu o il gruppo, proprio come si farebbe per un `Parent` elemento. È anche possibile impostare il `priority` attributo per stabilire la posizione relativa dell'elemento dell'interfaccia utente.  
  
 È possibile combinare posizionamento da genitorialità e posizionamento del comando. Tuttavia, per set di comandi di dimensioni molto grandi, è consigliabile usare solo commandplacement.  
  
### <a name="add-specialized-behaviors"></a>Aggiungere comportamenti di tipo specializzati  
 È possibile usare la [CommandFlag](../../extensibility/command-flag-element.md) elemento per modificare il comportamento del menu e comandi, ad esempio, per modificare l'aspetto e la visibilità. È possibile inoltre modificare quando un comando è visibile tramite il [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) elemento, o aggiungere tasti di scelta rapida utilizzando il [tasti di scelta rapida](../../extensibility/keybindings-element.md) elemento. Alcuni tipi di menu e comandi già avranno specializzati comportamenti predefiniti.  
  
#### <a name="to-add-specialized-behaviors"></a>Per aggiungere comportamenti di tipo specializzati  
  
1.  Per rendere visibili solo in determinati contesti dell'interfaccia utente, ad esempio, un elemento dell'interfaccia utente quando viene caricata una soluzione, usare i vincoli di visibilità.  
  
    1.  Dopo il `Commands` elemento, aggiungere un `VisibilityConstraints` elemento.  
  
    2.  Per ogni elemento dell'interfaccia utente applicare un vincolo, aggiungere un [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.  
  
    3.  Per ognuno `VisibilityItem` elemento, impostare il `guid` e `id` gli attributi per i menu, gruppo o comando e quindi impostare il `context` attributo al contesto dell'interfaccia utente desiderato, come definito nel <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classe.   
  
2.  Per impostare la visibilità o la disponibilità di un elemento dell'interfaccia utente nel codice, usare uno o più dei flag di comando seguenti:  
  
    -   `DefaultDisabled`
  
    -   `DefaultInvisible`
  
    -   `DynamicItemStart` 
  
    -   `DynamicVisibility`
  
    -   `NoShowOnMenuController`
  
    -   `NotInTBList`
  
   Per altre informazioni, vedere la [CommandFlag](../../extensibility/command-flag-element.md) elemento.  
  
3.  Per modificare la modalità di un elemento viene visualizzato o modificarne l'aspetto in modo dinamico, usare uno o più dei flag di comando seguenti:  
  
    -   `AlwaysCreate`  
  
    -   `CommandWellOnly`  
  
    -   `DefaultDocked`  
  
    -   `DontCache`  
  
    -   `DynamicItemStart`  
  
    -   `FixMenuController`  
  
    -   `IconAndText`  
  
    -   `Pict`  
  
    -   `StretchHorizontally`  
  
    -   `TextMenuUseButton`  
  
    -   `TextChanges`  
  
    -   `TextOnly`  
  
   Per altre informazioni, vedere la [CommandFlag](../../extensibility/command-flag-element.md) elemento.  
  
4.  Per modificare un elemento reazione quando riceve i comandi, usare uno o più dei flag di comando seguenti:  
  
    -   `AllowParams`  
  
    -   `CaseSensitive`  
  
    -   `CommandWellOnly`  
  
    -   `FilterKeys`  
  
    -   `NoAutoComplete`  
  
    -   `NoButtonCustomize`  
  
    -   `NoKeyCustomize`  
  
    -   `NoToolbarClose`  
  
    -   `PostExec`  
  
    -   `RouteToDocs`  
  
    -   `TextIsAnchorCommand`  
  
   Per altre informazioni, vedere la [CommandFlag](../../extensibility/command-flag-element.md) elemento.  
  
5.  Per collegare una dipendente dal menu di scelta rapida per un menu o un elemento in un menu, aggiungere un carattere e commerciale (&) nel `ButtonText` (elemento) per il menu o la voce di menu. Il carattere che segue la e commerciale è attiva tasti di scelta rapida quando viene aperto il menu padre.  
  
6.  Per collegare una tasto indipendenti dal menu di scelta rapida a un comando, usare il [tasti di scelta rapida](../../extensibility/keybindings-element.md) elemento. Per altre informazioni, vedere la [tasto di scelta rapida](../../extensibility/keybinding-element.md) elemento.  
  
7.  Per localizzare il testo del menu, usare il `LocCanonicalName` elemento. Per altre informazioni, vedere la [stringhe](../../extensibility/strings-element.md) elemento.  
  
 Alcuni tipi di menu e pulsante includere particolari funzionalità. L'elenco seguente descrive alcuni menu specializzato e tipi di pulsanti. Per altri tipi, vedere la `types` descrizioni, nell'attributo il [dal Menu](../../extensibility/menu-element.md), [pulsante](../../extensibility/button-element.md), e [combinata](../../extensibility/combo-element.md) elementi.  
  
 - Casella combinata:  
    Una casella combinata è un elenco di riepilogo a discesa che può essere utilizzato in una barra degli strumenti. Per aggiungere le caselle combinate all'interfaccia utente, creare un [Combos](../../extensibility/combos-element.md) elemento il `Commands` elemento. Quindi aggiungere il `Combos` elemento un `Combo` (elemento) per ogni casella combinata aggiungere. `Combo` gli elementi hanno gli stessi attributi e gli elementi figlio come `Button` elementi e avere `DefaultWidth` e `idCommandList` attributi. Il `DefaultWidth` attributo imposta la larghezza in pixel e il `idCommandList` attributo punti a un ID di comando che viene usato per popolare la casella combinata. 
  
 - Controller di menu:  
    Un controller di menu è un pulsante che dispone di una freccia accanto a esso. Facendo clic sulla freccia, viene aperto un elenco. Per aggiungere un controller di menu nell'interfaccia utente, creare un `Menu` e impostare relativi `type` dell'attributo `MenuController` o `MenuControllerLatched`, a seconda del comportamento desiderato. Per popolare un controller di menu, impostarlo come elemento padre di un `Group` elemento. Il controller di menu visualizzerà tutti gli elementi figlio di tale gruppo di nell'elenco a discesa elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere i menu e comandi](../../extensibility/extending-menus-and-commands.md)   
 [File di Visual Studio comando table (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)