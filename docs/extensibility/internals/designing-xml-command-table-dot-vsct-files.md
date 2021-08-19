---
title: Progettazione della tabella dei comandi XML (. Vsct) File | Microsoft Docs
description: Informazioni su come progettare un file di tabella dei comandi XML (con estensione vsct) che descrive il layout e l'aspetto degli elementi dei comandi, inclusi pulsanti, caselle combinate, menu e barre degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a3dc6aa48ef15e49928c87baeb913e18048a7e9e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102720"
---
# <a name="design-xml-command-table-vsct-files"></a>Progettare file di tabella dei comandi XML (con estensione vsct)
Un file di tabella dei comandi XML (*vsct*) descrive il layout e l'aspetto degli elementi di comando per un VSPackage. Gli elementi di comando includono pulsanti, caselle combinate, menu, barre degli strumenti e gruppi di elementi di comando. Questo articolo descrive i file della tabella dei comandi XML, il modo in cui influiscono sulle voci di comando e i menu e su come crearli.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandi, menu, gruppi e file con estensione vsct
 I *file vsct* sono organizzati in base a comandi, menu e gruppi di comandi. I tag XML nel file *con estensione vsct* rappresentano ognuno di questi elementi, insieme ad altri elementi associati, ad esempio pulsanti di comando, posizionamento dei comandi e bitmap.

 Quando si crea un nuovo VSPackage eseguendo il modello di pacchetto, il modello genera un file vsct con gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato, a seconda delle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] selezioni.  Questo file *con estensione vsct* può quindi essere modificato per soddisfare i requisiti di un pacchetto VSPackage specifico. Per esempi su come modificare un file *con estensione vsct,* vedere [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md).

 Per creare un nuovo file *vsct* vuoto, vedere [Procedura: Creare un file *vsct.*](../../extensibility/internals/how-to-create-a-dot-vsct-file.md) Dopo la creazione, si aggiungono elementi, attributi e valori XML al file per descrivere il layout dell'elemento di comando. Per uno schema XML dettagliato, vedere le informazioni di [riferimento sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Differenze tra i file con estensione ctc e vsct
 Anche se il significato dei tag XML in un file con estensione *vsct* è identico a quello dei tag nel formato di file *CTC* ora deprecato, la relativa implementazione è leggermente diversa:

- Il nuovo tag è il punto in cui si fa riferimento ad altri file con estensione h da compilare, ad esempio **\<extern>** i file per la barra degli  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] strumenti.

- Mentre *i file con estensione vsct* supportano l'istruzione **/include,** come fanno i file con estensione *ctc,* include anche un nuovo **\<import>** elemento. La differenza è che **/include** include *tutte* le informazioni, mentre **\<import>** contiene solo i nomi.

- Mentre *i file con estensione ctc* richiedono un file di intestazione in cui si definiscono le direttive per il preprocessore, non è necessario per i file con estensione *vsct.* Inserire invece le direttive nella tabella dei simboli, che si trova negli elementi , nella parte **\<Symbol>** inferiore del file con estensione *vsct.*

- *I file con estensione vsct* presentano un tag che consente di incorporare le informazioni che si desidera, ad esempio **\<Annotation>** note o persino immagini.

- I valori vengono archiviati come attributi nell'elemento.

- I flag di comando possono essere archiviati singolarmente o in pila.  IntelliSense, tuttavia, non funziona sui flag di comando in pila. Per altre informazioni sui flag di comando, vedere [l'elemento CommandFlag](../../extensibility/command-flag-element.md).

- È possibile specificare più tipi, ad esempio elenchi a discesa suddivisi, combinazioni e così via.

- I GUID non vengono convalidati.

- Ogni elemento dell'interfaccia utente ha una stringa che rappresenta il testo visualizzato con esso.

- L'elemento padre è facoltativo. Se omesso, viene usato *il valore Group Unknown.*

- *L'argomento Icon* è facoltativo.

- Sezione Bitmap: questa sezione è la stessa di un file con estensione *ctc,* con la differenza che è ora possibile specificare un nome di file tramite Href che verrà estratto dal compilatore *vsct.exein fase* di compilazione.

- ResID: l'ID risorsa bitmap precedente può essere usato e funziona comunque come nei *file con estensione ctc.*

- HRef: nuovo metodo che consente di specificare un nome file per la risorsa bitmap. Presuppone che tutti siano usati, quindi è possibile omettere la sezione Usato. Il compilatore cerca innanzitutto le risorse locali per il file, quindi in tutte le condivisioni net e le risorse definite **dall'opzione /I.**

- Keybinding: non è più necessario specificare un emulatore. Se ne specifica uno, il compilatore presuppone che l'editor e l'emulatore siano uguali.

- Keychord: il keychord è stato eliminato. Il nuovo formato è *Key1,Mod1,Key2,Mod2.*  È possibile specificare un carattere, una costante esadecimale o VK.

Il nuovo compilatore, *vsct.exe*, compila sia i file *con estensione ctc* che *vsct.* Il *compilatorectc.exe* precedente, tuttavia, non riconoscerà o compilerà *i file con estensione vsct.*

È possibile usare il *vsct.exe* per convertire un file *CTO* esistente in un file *con estensione vsct.* Per altre informazioni, vedere [Procedura: Creare un file vsct da un file CTO esistente.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)

## <a name="the-vsct-file-elements"></a>Elementi del file con estensione vsct
 La tabella dei comandi include la gerarchia e gli elementi seguenti:

- [Elemento CommandTable:](../../extensibility/commandtable-element.md)rappresenta tutti i comandi, i gruppi di menu e i menu associati al pacchetto VSPackage.

- [Elemento Extern](../../extensibility/extern-element.md): fa riferimento a tutti i file con estensione h esterni da unire al file *con estensione vsct.*

- [Elemento Include](../../extensibility/include-element.md): fa riferimento a tutti i file di intestazione aggiuntivi (con estensione h) che si desidera compilare insieme al file *con estensione vsct.* Un file *con estensione vsct* può includere file con estensione *h* contenenti costanti che definiscono comandi, gruppi di menu e menu forniti dall'IDE o da un altro pacchetto VSPackage.

- [Elemento Commands:](../../extensibility/commands-element.md)rappresenta tutti i singoli comandi che possono essere eseguiti. Ogni comando ha i quattro elementi figlio seguenti:

- [Elemento Menus:](../../extensibility/menus-element.md)rappresenta tutti i menu e le barre degli strumenti nel pacchetto VSPackage. I menu sono contenitori per gruppi di comandi.

- [Elemento Groups:](../../extensibility/groups-element.md)rappresenta tutti i gruppi nel pacchetto VSPackage. I gruppi sono raccolte di singoli comandi.

- [Elemento Buttons:](../../extensibility/buttons-element.md)rappresenta tutti i pulsanti di comando e le voci di menu nel pacchetto VSPackage. I pulsanti sono controlli visivi che possono essere associati ai comandi.

- [Elemento Bitmaps:](../../extensibility/bitmaps-element.md)rappresenta tutte le bitmap per tutti i pulsanti nel pacchetto VSPackage. Le bitmap sono immagini visualizzate accanto o sui pulsanti di comando, a seconda del contesto.

- [Elemento CommandPlacements](../../extensibility/commandplacements-element.md): indica posizioni aggiuntive in cui i singoli comandi devono essere presenti nei menu del pacchetto VSPackage.

- [Elemento VisibilityConstraints:](../../extensibility/visibilityconstraints-element.md)specifica se un comando viene visualizzato in qualsiasi momento o solo in determinati contesti, ad esempio quando viene visualizzata una determinata finestra di dialogo o finestra. I menu e i comandi che hanno un valore per questo elemento verranno visualizzati solo quando il contesto specificato è attivo. Il comportamento predefinito è visualizzare il comando in qualsiasi momento.

- [Elemento KeyBindings](../../extensibility/keybindings-element.md): specifica eventuali associazioni di tasti per i comandi. Ad esempio, una o più combinazioni di tasti che devono essere premute per eseguire il comando, ad esempio **CTRL** + **S.**

- [Elemento UsedCommands](../../extensibility/usedcommands-element.md): informa l'ambiente che, sebbene il comando specificato sia implementato da altro codice, quando il vspackage corrente è attivo, fornisce l'implementazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del comando.

- [Elemento Symbols](../../extensibility/symbols-element.md): contiene i nomi dei simboli e gli ID GUID per tutti i comandi nel pacchetto.

## <a name="vsct-file-design-guidelines"></a>Linee guida per la progettazione di file con estensione vsct
 Per progettare correttamente un file *vsct,* seguire queste linee guida.

- I comandi possono essere inseriti solo in gruppi, i gruppi possono essere inseriti solo nei menu e i menu possono essere inseriti solo in gruppi. Solo i menu vengono effettivamente visualizzati nell'IDE, i gruppi e i comandi non lo sono.

- I sottomenu non possono essere assegnati direttamente a un menu, ma devono essere assegnati a un gruppo, che a sua volta viene assegnato a un menu.

- Comandi, sottomenu e gruppi possono essere assegnati a un gruppo o a un menu padre usando il campo padre della direttiva di definizione.

- L'organizzazione di una tabella dei comandi solo tramite i campi padre nelle direttive presenta una limitazione significativa. Le direttive che definiscono gli oggetti possono richiedere un solo argomento padre.

- Il riutilizzo di comandi, gruppi o sottomenu richiede l'uso di una nuova direttiva per creare una nuova istanza dell'oggetto con una propria `GUID:ID` coppia.

- Ogni `GUID:ID` coppia deve essere univoca. Il riutilizzo di un comando che, ad esempio, è stato inserito in un menu, in una barra degli strumenti o in un menu di scelta rapida, viene gestito <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dall'interfaccia .

- I comandi e i sottomenu possono anche essere assegnati a più gruppi e i gruppi possono essere assegnati a più menu usando [l'elemento Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Note sul file con estensione vsct
 Se si apportano modifiche a un file con estensione *vsct* dopo la compilazione e la posizione in una DLL satellite nativa, è necessario eseguiredevenv.exe **/setup /nosetupvstemplates**. Questa operazione forza la rilettura delle risorse VSPackage specificate nel registro sperimentale e il database interno che descrive [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la ricompila.

 Durante lo sviluppo, è possibile creare e registrare più progetti VSPackage nell'hive sperimentale del Registro di sistema che può causare confusione nell'IDE. Per risolvere questo problema, è possibile ripristinare le impostazioni predefinite dell'hive sperimentale per rimuovere tutti i VSPackage registrati e le eventuali modifiche apportate all'IDE. Per reimpostare l'hive sperimentale, usare lo strumento CreateExpInstance.exe fornito con Visual Studio SDK. È possibile trovarlo in:

 *%PROGRAMFILES(x86)%\Visual Studio \\ \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Eseguire lo strumento usando il comando **CreateExpInstance /Reset**. Tenere presente che questo strumento rimuove dall'hive sperimentale tutti i VSPackage registrati non normalmente installati con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedi anche
- [Estendere menu e comandi](../../extensibility/extending-menus-and-commands.md)
