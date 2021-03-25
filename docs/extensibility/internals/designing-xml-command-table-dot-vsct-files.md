---
title: Progettazione della tabella comandi XML (. File vsct) | Microsoft Docs
description: Viene illustrato come progettare un file di tabella dei comandi XML (con estensione vsct) che descrive il layout e l'aspetto degli elementi di comando, inclusi pulsanti, caselle combinate, menu e barre degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d6409b5e624cd8596e669f191b2644aaf27a88c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090928"
---
# <a name="design-xml-command-table-vsct-files"></a>Progettare file della tabella dei comandi XML (con estensione vsct)
Un file della tabella dei comandi XML (con *estensione vsct*) descrive il layout e l'aspetto degli elementi del comando per un pacchetto VSPackage. Gli elementi di comando includono pulsanti, caselle combinate, menu, barre degli strumenti e gruppi di elementi di comando. Questo articolo descrive i file della tabella dei comandi XML, il modo in cui influiscono sugli elementi e sui menu del comando e su come crearli.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandi, menu, gruppi e file con estensione vsct
 I file con *estensione vsct* sono organizzati in tutti i comandi, i menu e i gruppi di comandi. I tag XML nel file con *estensione vsct* rappresentano ognuno di questi elementi, insieme ad altri elementi associati, ad esempio i pulsanti di comando, la posizione dei comandi e le bitmap.

 Quando si crea un nuovo pacchetto VSPackage eseguendo il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modello di pacchetto, il modello genera un file con *estensione vsct* con gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato, a seconda delle selezioni effettuate. Questo file con *estensione vsct* può quindi essere modificato per soddisfare i requisiti di un VSPackage specifico. Per esempi relativi alla modifica di un file con estensione *vsct* , vedere [estendere i menu e i comandi](../../extensibility/extending-menus-and-commands.md).

 Per creare un nuovo file con *estensione vsct* vuoto, vedere [procedura: creare un file con *estensione vsct*](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una volta creati, gli elementi, gli attributi e i valori XML vengono aggiunti al file per descrivere il layout dell'elemento del comando. Per un XML Schema dettagliato, vedere il [riferimento XML Schema vsct](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Differenze tra i file con estensione CTC e vsct
 Sebbene il significato alla base dei tag XML in un file con *estensione vsct* corrisponda a quello dei tag del formato di file *. CTC* ora deprecato, la loro implementazione è leggermente diversa:

- Il nuovo **\<extern>** tag è il punto in cui si fa riferimento ad altri file con *estensione h* da compilare, ad esempio i file per la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra degli strumenti.

- Sebbene i file con *estensione vsct* supportino l'istruzione **/include** , ad esempio i file con *estensione CTC* , presenta anche un nuovo **\<import>** elemento. La differenza è che **/include** introduce *tutte* le informazioni, mentre **\<import>** introduce solo i nomi.

- Sebbene i file con *estensione CTC* richiedano un file di intestazione in cui si definiscono le direttive per il preprocessore, non è necessario per i file con *estensione vsct* . Posizionare invece le direttive nella tabella dei simboli, che si trova negli **\<Symbol>** elementi, nella parte inferiore del file con *estensione vsct* .

- i file con *estensione vsct* includono un **\<Annotation>** tag che consente di incorporare le informazioni desiderate, ad esempio note o immagini.

- I valori vengono archiviati come attributi nell'elemento.

- I flag di comando possono essere archiviati singolarmente o in pila.  IntelliSense, tuttavia, non funziona sui flag di comando in pila. Per ulteriori informazioni sui flag di comando, vedere l' [elemento CommandFlag](../../extensibility/command-flag-element.md).

- È possibile specificare più tipi, ad esempio elenchi a discesa suddivisi, combinazioni e così via.

- I GUID non vengono convalidati.

- Ogni elemento dell'interfaccia utente dispone di una stringa che rappresenta il testo visualizzato.

- L'elemento padre è facoltativo. Se omesso, viene usato il gruppo di valori *Unknown* .

- L'argomento *Icon* è facoltativo.

- Sezione bitmap: questa sezione è identica a quella di un file con *estensione CTC* , ad eccezione del fatto che è ora possibile specificare un nome di file tramite href che verrà inserito dal compilatore *vsct.exe* in fase di compilazione.

- Da un Resid: è possibile usare l'ID di risorsa bitmap precedente e continuare a funzionare come nei file con *estensione CTC* .

- HRef: nuovo metodo che consente di specificare un nome di file per la risorsa bitmap. Si presuppone che vengano utilizzati tutti, quindi è possibile omettere la sezione utilizzata. Il compilatore cerca innanzitutto le risorse locali per il file, quindi in qualsiasi condivisione NET e tutte le risorse definite dall'opzione **/i** .

- Tasti di scelta: non è più necessario specificare un emulatore. Se ne viene specificato uno, il compilatore presuppone che l'editor e l'emulatore siano gli stessi.

- Sinchord: la combinazione di pulsanti è stata eliminata. Il nuovo formato è *Key1, Mod1, Key2, MOD2*.  È possibile specificare una costante character, esadecimale o VK.

Il nuovo compilatore, *vsct.exe*, compila entrambi i file *. CTC* e *. vsct* . Il vecchio *ctc.exe* compilatore, tuttavia, non riconoscerà né compilerà i file con *estensione vsct* .

È possibile usare il compilatore *vsct.exe* per convertire un file con estensione *CTO* esistente in un file con *estensione vsct* . Per altre informazioni, vedere [procedura: creare un file con estensione vsct da un file CTO esistente](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Elementi del file con estensione vsct
 La tabella dei comandi presenta la gerarchia e gli elementi seguenti:

- [Elemento CommandTable](../../extensibility/commandtable-element.md): rappresenta tutti i comandi, i gruppi di menu e i menu associati al pacchetto VSPackage.

- [Elemento extern](../../extensibility/extern-element.md): fa riferimento a tutti i file con estensione h esterni che si desidera unire con il file con *estensione vsct* .

- [Includi elemento](../../extensibility/include-element.md): fa riferimento a eventuali file di intestazione (. h) aggiuntivi che si desidera compilare insieme al file con *estensione vsct* . Un file con *estensione vsct* può includere file con *estensione h* contenenti costanti che definiscono i comandi, i gruppi di menu e i menu forniti dall'IDE o da un altro VSPackage.

- [Commands-elemento](../../extensibility/commands-element.md): rappresenta tutti i singoli comandi che possono essere eseguiti. Ogni comando ha i quattro elementi figlio seguenti:

- [Elemento menus](../../extensibility/menus-element.md): rappresenta tutti i menu e le barre degli strumenti in VSPackage. I menu sono contenitori per gruppi di comandi.

- [Groups-elemento](../../extensibility/groups-element.md): rappresenta tutti i gruppi nel pacchetto VSPackage. I gruppi sono raccolte di singoli comandi.

- [Buttons-elemento](../../extensibility/buttons-element.md): rappresenta tutti i pulsanti di comando e le voci di menu nel pacchetto VSPackage. I pulsanti sono controlli visivi che possono essere associati ai comandi.

- [Bitmaps (elemento](../../extensibility/bitmaps-element.md)): rappresenta tutte le bitmap per tutti i pulsanti nel pacchetto VSPackage. Le bitmap sono immagini visualizzate accanto ai pulsanti di comando, a seconda del contesto.

- [Elemento CommandPlacements](../../extensibility/commandplacements-element.md): indica percorsi aggiuntivi in cui i singoli comandi devono essere collocati nei menu del pacchetto VSPackage.

- [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md): specifica se un comando viene visualizzato in qualsiasi momento o solo in determinati contesti, ad esempio quando viene visualizzata una finestra di dialogo o una finestra di dialogo specifica. I menu e i comandi che hanno un valore per questo elemento vengono visualizzati solo quando il contesto specificato è attivo. Il comportamento predefinito prevede la visualizzazione del comando in qualsiasi momento.

- [Bindings element](../../extensibility/keybindings-element.md): specifica le combinazioni di tasti per i comandi. Ovvero una o più combinazioni di tasti che devono essere premuti per eseguire il comando, ad esempio **CTRL** + **S**.

- [Elemento UsedCommands](../../extensibility/usedcommands-element.md): informa l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente che, sebbene il comando specificato venga implementato da altro codice, quando il pacchetto VSPackage corrente è attivo, fornisce l'implementazione del comando.

- [Symbols-elemento](../../extensibility/symbols-element.md): contiene i nomi dei simboli e gli ID GUID per tutti i comandi nel pacchetto.

## <a name="vsct-file-design-guidelines"></a>linee guida per la progettazione di file con estensione vsct
 Per progettare correttamente un file con *estensione vsct* , attenersi alle indicazioni seguenti.

- I comandi possono essere inseriti solo in gruppi, i gruppi possono essere inseriti solo nei menu e i menu possono essere inseriti solo in gruppi. Solo i menu vengono effettivamente visualizzati nell'IDE, i gruppi e i comandi non lo sono.

- I sottomenu non possono essere assegnati direttamente a un menu, ma devono essere assegnati a un gruppo, che a sua volta viene assegnato a un menu.

- I comandi, i sottomenu e i gruppi possono essere assegnati a un gruppo o a un menu padre utilizzando il campo padre della relativa direttiva di definizione.

- L'organizzazione di una tabella dei comandi esclusivamente tramite i campi padre nelle direttive presenta una limitazione significativa. Le direttive che definiscono gli oggetti possono assumere un solo argomento padre.

- Per riutilizzare i comandi, i gruppi o i sottomenu è necessario utilizzare una nuova direttiva per creare una nuova istanza dell'oggetto con una propria `GUID:ID` coppia.

- Ogni `GUID:ID` coppia deve essere univoca. Il riutilizzo di un comando che, ad esempio, è stato inserito in un menu, una barra degli strumenti o in un menu di scelta rapida, viene gestito dall' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.

- I comandi e i sottomenu possono anche essere assegnati a più gruppi e i gruppi possono essere assegnati a più menu usando l' [elemento Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Note sul file con estensione vsct
 Se si apportano modifiche a un file con *estensione vsct* dopo che è stato compilato e inserito in una DLL satellite nativa, è necessario eseguire **devenv.exe/Setup/nosetupvstemplates**. Questa operazione impone la rilettura delle risorse VSPackage specificate nel registro di sistema sperimentale e il database interno che descrive [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per essere ricompilato.

 Durante lo sviluppo, è possibile creare e registrare più progetti VSPackage nell'hive del registro di sistema sperimentale che può causare confusione nell'IDE. Per risolvere questo problema, è possibile reimpostare l'hive sperimentale sulle impostazioni predefinite per rimuovere tutti i pacchetti VSPackage registrati e le eventuali modifiche apportate all'IDE. Per reimpostare l'hive sperimentale, usare lo strumento CreateExpInstance.exe incluso in Visual Studio SDK. È possibile trovarlo all'indirizzo:

 *% PROGRAMFILES (x86)% \ Visual Studio \\ \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Eseguire lo strumento usando il comando **CreateExpInstance/Reset**. Tenere presente che questo strumento rimuove dall'hive sperimentale tutti i pacchetti VSPackage registrati normalmente non installati con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedi anche
- [Estendi menu e comandi](../../extensibility/extending-menus-and-commands.md)
