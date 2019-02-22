---
title: Progettazione di tabella comandi XML (. File Vsct) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a833478a8dec3b9fe82b22295482fed6f5562d14
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641546"
---
# <a name="design-xml-command-table-vsct-files"></a>Progettare i file XML comando table (vsct)
Una tabella comandi XML (*vsct*) file descrive il layout e l'aspetto degli elementi di comando per un pacchetto VSPackage. Gli elementi di comando includono i pulsanti, caselle combinate, menu, barre degli strumenti e i gruppi di voci di comando. Questo articolo descrive XML comando tabella file, modo influiscano menu e voci di comando e come crearli.

## <a name="commands-menus-groups-and-the-vsct-file"></a>I comandi, menu, gruppi e i file con estensione vsct
 Il *vsct* file organizzati in gruppi di comandi, menu e comandi. Tag XML nel *vsct* file rappresentano ciascuno di questi elementi, insieme agli altri elementi associati, ad esempio i pulsanti di comando, commandplacement e bitmap.

 Quando si crea un nuovo pacchetto di Visual Studio eseguendo la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modello di pacchetto, il modello genera un *vsct* file con gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato dipendono dalle selezioni. Ciò *vsct* file può quindi essere modificato per soddisfare i requisiti di un VSPackage specifico. Per esempi su come modificare un *vsct* del file, vedere [estendono i menu e comandi](../../extensibility/extending-menus-and-commands.md).

 Per creare una nuova, spegnere *vsct* del file, vedere [come: Creare un *vsct* file](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una volta creata, aggiungere elementi, attributi e valori XML nel file per descrivere il layout dell'elemento di comando. Per uno schema XML dettagliato, vedere la [riferimenti allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Differenze tra file con estensione CTC e con estensione vsct
 Mentre il significato dietro il codice XML dei tag un *vsct* file corrispondono a tali tag nell'ora deprecata *CTC* formato di file, l'implementazione è leggermente diversa:

- Il nuovo  **\<extern >** tag è in cui si fa riferimento altri *. h* file da compilare, ad esempio i file per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sulla barra degli strumenti.

- Mentre *vsct* i file di supporto di **/include** istruzione, come *CTC* tale file, include anche un nuovo  **\<importare >** elemento. È la differenza, **/include** riporta *tutti i* delle informazioni, mentre  **\<importare >** Importa solo i nomi.

- Sebbene *CTC* file richiedono un file di intestazione in cui si definiscono le direttive del preprocessore, uno non è necessario per *con estensione vsct* file. Invece di inserire le direttive nella tabella dei simboli, che si trova nel  **\<simbolo >** elementi, che si trova nella parte inferiore della *vsct* file.

- *con estensione vsct* funzionalità dei file per un  **\<Annotation >** tag, che consente di incorporare qualsiasi informazione desiderata, ad esempio note o persino le immagini.

- I valori vengono archiviati come attributi dell'elemento.

- Flag dei comandi può essere archiviato singolarmente o in pila.  IntelliSense, tuttavia, non funziona sui flag di comando in pila. Per altre informazioni sui flag di comando, vedere la [elemento CommandFlag](../../extensibility/command-flag-element.md).

- È possibile specificare più tipi, ad esempio elenchi a discesa split combos, e così via.

- I GUID non vengono convalidati.

- Ogni elemento dell'interfaccia utente è una stringa che rappresenta il testo visualizzato con esso.

- L'elemento padre è facoltativo. Se omesso, il valore *gruppo sconosciuto* viene usato.

- Il *icona* argomento è facoltativo.

- Sezione bitmap: In questa sezione è lo stesso di un *CTC* nel file, ad eccezione del fatto che è ora possibile specificare un nome di file tramite Href estratti in per il *vsct.exe* compilatore in fase di compilazione.

- ResID: La vecchia risorsa ID può essere utilizzato e comunque funziona come in bitmap *CTC* file.

- HRef: Un nuovo metodo che consente di specificare un nome file per la risorsa della bitmap. Si presuppone che tutte siano utilizzate, in modo che è possibile omettere la sezione utilizzata. Il compilatore eseguirà la ricerca prima di tutto per le risorse locali per il file, quindi su tutte le condivisioni di rete e tutte le risorse definite per il **/I** passare.

- Tasto di scelta rapida: È non è più necessario specificare un emulatore. Se si specifica uno, il compilatore presuppone che l'editor e l'emulatore sono uguali.

- Keychord: Keychord è stato eliminato. Il nuovo formato viene *Key1, Mod1, Key2, Mod2*.  È possibile specificare un carattere, esadecimale o costante VK.

Il nuovo compilatore *vsct.exe*, consente di compilare entrambe *CTC* e *vsct* file. Il vecchio *ctc.exe* compilatore, tuttavia, non riconosce o compilare *con estensione vsct* file.

È possibile usare la *vsct.exe* compilatore di convertire un oggetto esistente *CTO* del file in un *vsct* file. Per altre informazioni, vedere [Procedura: Creare un file con estensione vsct da un file CTO esistente](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Elementi del file con estensione vsct
 Nella tabella del comando ha la gerarchia e gli elementi seguenti:

- [Elemento CommandTable](../../extensibility/commandtable-element.md): Rappresenta tutti i comandi, gruppi di menu e menu associati al pacchetto VSPackage.

- [Elemento extern](../../extensibility/extern-element.md): Fa riferimento a tutti i file con estensione h esterno che si desidera eseguire il merge con il *vsct* file.

- [L'elemento di inclusione](../../extensibility/include-element.md): Fa riferimento a qualsiasi file di intestazione aggiuntivi (con estensione h) che si desidera compilare con il *vsct* file. Oggetto *vsct* file può includere *h* file contenenti le costanti che definiscono i comandi, gruppi di menu e menu che l'IDE o un altro VSPackage fornisce.

- [Elemento Commands](../../extensibility/commands-element.md): Rappresenta tutti i singoli comandi che possono essere eseguiti. Ogni comando presenta i quattro elementi figlio seguenti:

- [Elemento Menus](../../extensibility/menus-element.md): Rappresenta tutti i menu e barre degli strumenti in VSPackage. I menu sono contenitori per i gruppi di comandi.

- [Elemento Groups](../../extensibility/groups-element.md): Rappresenta tutti i gruppi nel pacchetto VSPackage. I gruppi sono raccolte di singoli comandi.

- [Elemento Buttons](../../extensibility/buttons-element.md): Rappresenta tutti i pulsanti di comando e voci di menu nel pacchetto VSPackage. I pulsanti sono controlli visivi che possono essere associati a comandi.

- [Elemento Bitmaps](../../extensibility/bitmaps-element.md): Rappresenta tutte le bitmap per tutti i pulsanti nel pacchetto VSPackage. Le bitmap sono immagini che vengono visualizzate accanto a o sui pulsanti di comando, a seconda del contesto.

- [Elemento CommandPlacements](../../extensibility/commandplacements-element.md): Indica i percorsi aggiuntivi in cui devono essere posizionati i singoli comandi nei menu del pacchetto VSPackage.

- [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md): Specifica se un comando vengono visualizzati affatto volte o solo in determinati contesti, ad esempio quando viene visualizzata una finestra di dialogo specifico o una finestra. Menu e comandi che hanno un valore per questo elemento verranno visualizzato solo quando il contesto specificato è attivo. Il comportamento predefinito è per visualizzare il comando in qualsiasi momento.

- [Elemento KeyBindings](../../extensibility/keybindings-element.md): Specifica qualsiasi tasti di scelta rapida per i comandi. Vale a dire, una o più combinazioni di tasti da premere per eseguire il comando, ad esempio **Ctrl**+**S**.

- [Elemento UsedCommands](../../extensibility/usedcommands-element.md): Informa il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente anche se il comando specificato è implementato da altro codice, quando il pacchetto VSPackage corrente è attivo, fornisce l'implementazione del comando.

- [Elemento symbols](../../extensibility/symbols-element.md): Contiene i nomi dei simboli e gli ID di GUID per tutti i comandi nel pacchetto.

## <a name="vsct-file-design-guidelines"></a>linee guida di progettazione di file con estensione vsct
 Per progettare correttamente un *vsct* file, seguire queste linee guida.

-   Comandi possono essere posizionati solo in gruppi, i gruppi possono essere inseriti solo nei menu e menu possono essere posizionati solo in gruppi. Solo i menu sono effettivamente visualizzati nell'IDE, gruppi e i comandi non lo sono.

-   Sottomenu non possono essere assegnati direttamente a un menu, ma devono essere assegnati a un gruppo, che a sua volta viene assegnato a un menu.

-   I comandi, sottomenu e gruppi assegnabili a un gruppo padre o menu usando il campo padre della loro definizione direttiva.

-   Organizzazione di una tabella comandi esclusivamente tramite i campi padre nelle direttive di ha un limite significativo. Le direttive che definiscono gli oggetti possono accettare un solo padre argomento.

-   Riutilizzo di comandi, gruppi o sottomenu richiede l'uso di una direttiva di nuovo per creare una nuova istanza dell'oggetto con il proprio `GUID:ID` coppia.

-   Ogni `GUID:ID` coppia deve essere univoca. Riutilizzo di un comando, ad esempio, situato in un menu, una barra degli strumenti o in un menu di scelta rapida viene gestito dal <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.

-   Comandi sia sottomenu possono anche essere assegnati a più gruppi e i gruppi possono essere assegnati a più menu usando la [elemento Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>note di file con estensione vsct
 Se si apportano modifiche a un *vsct* file dopo che si sia compilarlo e inserirlo in una DLL satellite nativa, è consigliabile eseguire **devenv.exe /setup /nosetupvstemplates**. Esegue in questo caso impone le risorse di VSPackage specificate nel Registro di sistema sperimentale per essere rilettura e il database interno che descrive [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da ricompilare.

 Durante lo sviluppo, è possibile per più progetti VSPackage venga creato e registrato nell'hive del Registro di sistema sperimentale che può provocare confusione confusione nell'IDE. Per risolvere questo problema, è possibile reimpostare l'hive sperimentale per le impostazioni predefinite per rimuovere registrati tutti i pacchetti VSPackage e le eventuali modifiche apportate all'IDE. Per reimpostare l'hive sperimentale, usare lo strumento CreateExpInstance.exe fornito con Visual Studio SDK. È possibile trovarlo in:

 *%PROGRAMFILES(x86)%\Visual Studio\\\<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Eseguire lo strumento usando il comando **CreateExpInstance /Reset**. Tenere presente che questo strumento rimuove da hive sperimentale tutti i pacchetti VSPackage registrati che normalmente non vengono installati con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vedere anche
- [Estendere i menu e comandi](../../extensibility/extending-menus-and-commands.md)