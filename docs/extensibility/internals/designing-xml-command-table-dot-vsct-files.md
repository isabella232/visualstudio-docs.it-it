---
title: Progettazione della tabella dei comandi XML (. File di Vsct) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708746"
---
# <a name="design-xml-command-table-vsct-files"></a>Progettare file di tabella dei comandi XML (con estensione vsct)
Un file della tabella dei comandi XML (*vsct*) descrive il layout e l'aspetto degli elementi di comando per un pacchetto VSPackage. Gli elementi di comando includono pulsanti, caselle combinate, menu, barre degli strumenti e gruppi di elementi di comando. In questo articolo vengono descritti i file della tabella dei comandi XML, il modo in cui influiscono sugli elementi di comando e i menu e come crearli.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandi, menu, gruppi e il file vsct
 I file *vsct* sono organizzati in base a comandi, menu e gruppi di comandi. I tag XML nel file *vsct* rappresentano ognuno di questi elementi, insieme ad altri elementi associati, ad esempio pulsanti di comando, posizionamento dei comandi e bitmap.

 Quando si crea un nuovo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vsPackage eseguendo il modello di pacchetto, il modello genera un file *con estensione vsct* con gli elementi necessari per un comando di menu, finestra degli strumenti o editor personalizzato, a seconda delle selezioni. Questo file *vsct* può quindi essere modificato per soddisfare i requisiti di un pacchetto VSPackage specifico. Per esempi su come modificare un file *vsct,* vedere [Estendere menu e comandi.](../../extensibility/extending-menus-and-commands.md)

 Per creare un nuovo file *vsct* vuoto, vedere [Procedura: creare un file *vsct* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una volta creati, aggiungere elementi, attributi e valori XML al file per descrivere il layout dell'elemento di comando. Per uno schema XML dettagliato, vedere le informazioni di [riferimento sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Differenze tra i file con estensione ctc e vsct
 Mentre il significato dietro i tag XML in un file *.vsct* sono gli stessi di quei tag nel formato di file *.ctc* ora deprecato, la loro implementazione è un po 'diverso:

- Il nuovo *.h* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ** \<tag>extern** è il punto in cui si fa riferimento ad altri file con estensione h da compilare, ad esempio i file per la barra degli strumenti.

- Mentre i file *vsct* supportano l'istruzione **/include,** come fanno i file *.ctc,* è anche dotato di un nuovo ** \<** elemento di>di importazione. La differenza è che **/include** include *tutte le* informazioni, mentre ** \<l'importazione>** porta solo i nomi.

- Mentre i file *.ctc* richiedono un file di intestazione in cui si definiscono le direttive del preprocessore, uno non è necessario per i file *vsct.* Posizionare invece le direttive nella tabella dei simboli, che si trova nel ** \<simbolo>** elementi, che si trova nella parte inferiore del file *vsct.*

- I file *.vsct* presentano un ** \<** tag di>di annotazione, che consente di incorporare tutte le informazioni desiderate, ad esempio note o persino immagini.

- I valori vengono archiviati come attributi nell'elemento.

- I flag di comando possono essere archiviati singolarmente o impilati.  IntelliSense, tuttavia, non funziona sui flag di comando in pila. Per ulteriori informazioni sui flag di comando, vedere [l'elemento CommandFlag](../../extensibility/command-flag-element.md).

- È possibile specificare più tipi, ad esempio elenchi a discesa divisi, combinazioni e così via.

- I GUID non vengono convalidati.

- Ogni elemento dell'interfaccia utente ha una stringa che rappresenta il testo visualizzato con esso.

- L'elemento padre è facoltativo. Se omesso, viene utilizzato il valore *Gruppo sconosciuto.*

- L'argomento *Icon* è facoltativo.

- Sezione Bitmap: questa sezione è la stessa di un file *.ctc,* ad eccezione del fatto che ora è possibile specificare un nome di file tramite Href che verrà estratto dal compilatore *vsct.exe* in fase di compilazione.

- ResID: il vecchio ID di risorsa bitmap può essere utilizzato e funziona comunque come nei file *.ctc.*

- HRef: un nuovo metodo che consente di specificare un nome di file per la risorsa bitmap. Si presuppone che vengano utilizzati tutti, pertanto è possibile omettere la sezione Usato. Il compilatore cercherà innanzitutto le risorse locali per il file, quindi in tutte le condivisioni di rete e tutte le risorse definite dall'opzione **/I.**

- Associazione di tasti: non è più necessario specificare un emulatore. Se ne specifichi uno, il compilatore presupporrà che l'editor e l'emulatore siano uguali.

- Keychord: Keychord è stato eliminato. Il nuovo formato è *Key1,Mod1,Key2,Mod2*.  È possibile specificare un carattere, un valore esadecimale o una costante VK.

Il nuovo compilatore, *vsct.exe*, compila i file *con estensione ctc* e *vsct.* Il compilatore *ctc.exe* precedente, tuttavia, non riconoscerà o compilerà i file *vsct.*

È possibile utilizzare il compilatore *vsct.exe* per convertire un file *con estensione cto* esistente in un file *con estensione vsct.* Per ulteriori informazioni, vedere [Procedura: creare un file vsct da un file con estensione cto esistente.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)

## <a name="the-vsct-file-elements"></a>Elementi del file vsct
 La tabella dei comandi ha la gerarchia e gli elementi seguenti:

- [Elemento CommandTable](../../extensibility/commandtable-element.md): rappresenta tutti i comandi, i gruppi di menu e i menu associati al pacchetto VSPackage.

- [Extern element](../../extensibility/extern-element.md): Fa riferimento a tutti i file h esterni che si desidera unire al file *vsct.*

- [Include element](../../extensibility/include-element.md): Fa riferimento a qualsiasi file di intestazione (h) aggiuntivo che si desidera compilare insieme al file *vsct.* Un file *con estensione vsct* può includere file *con estensione h* contenenti costanti che definiscono i comandi, gruppi di menu e menu che fornisce l'IDE o un altro VSPackage.

- [Commands element](../../extensibility/commands-element.md): Rappresenta tutti i singoli comandi che possono essere eseguiti. Ogni comando ha i seguenti quattro elementi figlio:

- [Menus elemento](../../extensibility/menus-element.md): Rappresenta tutti i menu e le barre degli strumenti nel pacchetto VSPackage. I menu sono contenitori per gruppi di comandi.

- [Elemento Groups](../../extensibility/groups-element.md): Rappresenta tutti i gruppi nel pacchetto VSPackage. I gruppi sono raccolte di singoli comandi.

- [Elemento Buttons](../../extensibility/buttons-element.md): Rappresenta tutti i pulsanti di comando e le voci di menu nel pacchetto VSPackage. I pulsanti sono controlli visivi che possono essere associati ai comandi.

- [Elemento Bitmaps](../../extensibility/bitmaps-element.md): rappresenta tutte le bitmap per tutti i pulsanti nel pacchetto VSPackage. Le bitmap sono immagini che vengono visualizzate accanto o sui pulsanti di comando, a seconda del contesto.

- [CommandPlacements elemento](../../extensibility/commandplacements-element.md): indica posizioni aggiuntive in cui i singoli comandi devono essere individuati nei menu del pacchetto VSPackage.

- [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md): Specifica se un comando viene visualizzato o meno in qualsiasi momento o solo in determinati contesti, ad esempio quando viene visualizzata una finestra di dialogo o una finestra specifica. I menu e i comandi che hanno un valore per questo elemento verranno visualizzati solo quando il contesto specificato è attivo. Il comportamento predefinito prevede la visualizzazione del comando in qualsiasi momento.

- [Elemento KeyBindings](../../extensibility/keybindings-element.md): specifica eventuali associazioni di tasti per i comandi. Ovvero, una o più combinazioni di tasti che devono essere premute per eseguire il comando, ad esempio **Ctrl**+**S**.

- [UsedCommands (elemento):](../../extensibility/usedcommands-element.md) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informa l'ambiente che, anche se il comando specificato viene implementato da altro codice, quando il pacchetto VSPackage corrente è attivo, fornisce l'implementazione del comando.

- [Elemento Symbols](../../extensibility/symbols-element.md): Contiene i nomi dei simboli e gli ID GUID per tutti i comandi nel pacchetto.

## <a name="vsct-file-design-guidelines"></a>Linee guida per la progettazione di file .vsct
 Per progettare correttamente un file *vsct,* seguire queste linee guida.

- I comandi possono essere posizionati solo in gruppi, i gruppi possono essere posizionati solo nei menu e i menu possono essere inseriti solo in gruppi. Solo i menu vengono effettivamente visualizzati nell'IDE, gruppi e comandi non lo sono.

- I sottomenu non possono essere assegnati direttamente a un menu, ma devono essere assegnati a un gruppo, che a sua volta viene assegnato a un menu.

- I comandi, i sottomenu e i gruppi possono essere assegnati a un gruppo o a un menu padre utilizzando il campo padre della relativa direttiva di definizione.

- L'organizzazione di una tabella di comandi esclusivamente tramite i campi padre nelle direttive presenta una limitazione significativa. Le direttive che definiscono gli oggetti possono accettare un solo argomento padre.

- Il riutilizzo di comandi, gruppi o sottomenu richiede l'utilizzo di una nuova `GUID:ID` direttiva per creare una nuova istanza dell'oggetto con la propria coppia.

- Ogni `GUID:ID` coppia deve essere univoca. Il riutilizzo di un comando che, ad esempio, è stato inserito in un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> menu, una barra degli strumenti o un menu di scelta rapida, viene gestito dall'interfaccia.

- I comandi e i sottomenu possono anche essere assegnati a più gruppi e i gruppi possono essere assegnati a più menu utilizzando [l'elemento Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Note del file vsct
 Se si apportano modifiche a un file *vsct* dopo averlo compilato e averlo inserito in una DLL satellite nativa, è necessario eseguire **devenv.exe /setup /nosetupvstemplates**. In questo modo forza le risorse VSPackage specificate nel Registro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sistema sperimentale da rileggere e il database interno che descrive per essere ricompilato.

 Durante lo sviluppo, è possibile per più progetti VSPackage da creare e registrare nell'hive del Registro di sistema sperimentale che può causare confusione nell'IDE. Per risolvere questo problema, è possibile reimpostare l'hive sperimentale alle impostazioni predefinite per rimuovere tutti i pacchetti VSPackage registrati e le eventuali modifiche apportate all'IDE. Per reimpostare l'hive sperimentale, utilizzare lo strumento CreateExpInstance.exe fornito con Visual Studio SDK. Puoi trovarlo all':

 *%PROGRAMFILES(x86)%%versione\\\<di Visual Studio> SDK*

 Eseguire lo strumento utilizzando il comando **CreateExpInstance /Reset**. Tenere presente che questo strumento rimuove dall'hive sperimentale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tutti i pacchetti VS registrati non normalmente installati con .

## <a name="see-also"></a>Vedere anche
- [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md)
