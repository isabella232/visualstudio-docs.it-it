---
title: Progettazione di tabella comandi XML (. File Vsct) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb75a161feffa049ebf7152d6a76d70f364a98ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229385"
---
# <a name="designing-xml-command-table-vsct-files"></a>Progettazione di tabella comandi XML (. File Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un file XML comando table (vsct) descrive il layout e l'aspetto degli elementi di comando per un pacchetto VSPackage. Gli elementi di comando includono i pulsanti, caselle combinate, menu, barre degli strumenti e i gruppi di voci di comando. In questo argomento viene descritto XML comando tabella file, modo influiscano menu e voci di comando e come crearli.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>I comandi, menu, gruppi e i File con estensione vsct  
 i file con estensione vsct organizzati in gruppi di comandi, menu e comandi. I tag XML nel file con estensione vsct rappresentano ognuno di questi elementi, insieme agli altri elementi associati, ad esempio i pulsanti di comando, commandplacement e bitmap.  
  
 Quando si crea un nuovo pacchetto di Visual Studio eseguendo la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] modello di pacchetto, il modello genera un file con estensione vsct con gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato dipendono dalle selezioni. Questo file con estensione vsct può quindi essere modificato per soddisfare i requisiti di un VSPackage specifico. Per esempi di come modificare un file vsct, vedere gli esempi inclusi in [estensione di menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Per creare un file con estensione vsct vuoto, vedere [procedura: creare una. File Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una volta creata, aggiungere elementi, attributi e valori XML nel file per descrivere il layout dell'elemento di comando. Per uno schema XML dettagliato, vedere la [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Differenze tra file con estensione CTC e con estensione vsct  
 Mentre il significato di tag XML in un file con estensione vsct è uguali come quelle nell'ora deprecato il formato di file con estensione CTC, l'implementazione è leggermente diversa.  
  
-   Il nuovo  **\<extern >** tag è in cui si fa riferimento altri file. h deve essere compilato, ad esempio quelli per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sulla barra degli strumenti.  
  
-   Mentre il supporto di file con estensione vsct il **/include** istruzione, come file con estensione CTC, anche una nuova funzionalità denominata \< **importare >** elemento. È la differenza, **/include** riporta **tutti i** delle informazioni, ma \< **importare >** Importa solo i nomi.  
  
-   Mentre i file con estensione CTC richiedono un file di intestazione in cui si definiscono le direttive del preprocessore, uno non è necessario per i file con estensione vsct. In alternativa, inserire le direttive nella tabella dei simboli, che si trova nel  **\<simbolo >** elementi, che si trova nella parte inferiore del file con estensione vsct.  
  
-   funzionalità dei file con estensione vsct un'  **\<Annotation >** tag, che consente di incorporare qualsiasi informazione desiderata, ad esempio note o persino le immagini.  
  
-   I valori vengono archiviati come attributi dell'elemento.  
  
-   Flag dei comandi può essere archiviato singolarmente o in pila.  IntelliSense, tuttavia, non funziona sui flag di comando in pila. Per altre informazioni sui flag di comando, vedere la [elemento Commandflag](../../extensibility/command-flag-element.md).  
  
-   È possibile specificare più tipi, ad esempio elenchi a discesa split combos, e così via.  
  
-   I GUID non vengono convalidati.  
  
-   Ogni elemento dell'interfaccia utente è una stringa che rappresenta il testo visualizzato con esso.  
  
-   Elemento padre è facoltativo. Se omesso, viene utilizzato il valore "Gruppo" sconosciuto".  
  
-   L'icona di argomento è facoltativa.  
  
-   La sezione bitmap, ovvero lo stesso come un CTC file, ad eccezione del fatto che è ora possibile specificare un nome di file tramite href che vengono spostate dal compilatore vsct.exe in fase di compilazione.  
  
-   ResID: l'ID della risorsa bitmap precedente può essere usato e comunque funziona esattamente come nel file con estensione CTC.  
  
-   HRef - un nuovo metodo che consente di specificare un nome file per la risorsa della bitmap. Si presuppone che tutte siano utilizzate, in modo che è possibile omettere la sezione utilizzata. Il compilatore eseguirà la ricerca prima di tutto per le risorse locali per il file, quindi su tutte le condivisioni di rete e tutte le risorse definite dal commutatore /I.  
  
-   Tasto di scelta rapida, È non è più necessario specificare un emulatore. Se si specifica uno, il compilatore presuppone che l'editor e l'emulatore sono uguali.  
  
-   Keychord - è stato eliminato. Il nuovo formato è Key1, Mod1, Key2, Mod2.  È possibile specificare un carattere, esadecimale o costante VK.  
  
 Il nuovo compilatore, vsct.exe, compilare i file con estensione CTC sia con estensione vsct. Il compilatore ctc.exe precedente, tuttavia, verrà non riconosce né compilare i file con estensione vsct.  
  
 È possibile usare il compilatore vsct.exe per convertire un file CTO esistente in un file con estensione vsct. Per altre informazioni, vedere [procedura: creare una. File Vsct da un oggetto esistente. File CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Elementi del File con estensione vsct  
 Nella tabella del comando ha la gerarchia e gli elementi seguenti:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) : rappresenta tutti i comandi, gruppi di menu e menu associati al pacchetto VSPackage.  
  
 [Elemento extern](../../extensibility/extern-element.md) : fa riferimento a tutti i file con estensione h esterno che si desidera eseguire il merge con il file con estensione vsct.  
  
 [L'elemento di inclusione](../../extensibility/include-element.md) : fa riferimento a qualsiasi file di intestazione aggiuntivi (con estensione h) che si desidera compilare insieme your.vsct file. Un file con estensione vsct può includere file con estensione h che contiene le costanti che definiscono i comandi, gruppi di menu e menu che fornisce l'IDE o un altro pacchetto VSPackage.  
  
 [Comandi elemento](../../extensibility/commands-element.md) : rappresenta tutti i singoli comandi che possono essere eseguiti. Ogni comando presenta i quattro elementi figlio seguenti:  
  
 [Elemento Menus](../../extensibility/menus-element.md) : rappresenta tutti i menu e barre degli strumenti in VSPackage. I menu sono contenitori per i gruppi di comandi.  
  
 [Gruppi elemento](../../extensibility/groups-element.md) : rappresenta tutti i gruppi nel pacchetto VSPackage. I gruppi sono raccolte di singoli comandi.  
  
 [Pulsanti elemento](../../extensibility/buttons-element.md) : rappresenta tutti i pulsanti di comando e voci di menu nel pacchetto VSPackage. I pulsanti sono controlli visivi che possono essere associati a comandi.  
  
 [Elemento Bitmaps](../../extensibility/bitmaps-element.md) : rappresenta tutte le bitmap per tutti i pulsanti nel pacchetto VSPackage. Le bitmap sono immagini che vengono visualizzate accanto a o sui pulsanti di comando, a seconda del contesto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) — indica altri percorsi in cui devono essere posizionati i singoli comandi nei menu del pacchetto VSPackage.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) : Specifica se un comando consente di visualizzare affatto volte o solo in determinati contesti, ad esempio quando viene visualizzata una finestra di dialogo specifico o una finestra. Menu e comandi che hanno un valore per questo elemento verranno visualizzato solo quando il contesto specificato è attivo. Il comportamento predefinito è per visualizzare il comando in qualsiasi momento.  
  
 [Elemento KeyBindings](../../extensibility/keybindings-element.md) : specifica qualsiasi tasti di scelta rapida per i comandi. Vale a dire, una o più combinazioni di tasti da premere per eseguire il comando, ad esempio **CTRL + S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) , ovvero Informs il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente anche se il comando specificato è implementato da altro codice, quando il pacchetto VSPackage corrente è attivo, fornisce l'implementazione del comando.  
  
 `Symbols Element` : Contiene i nomi dei simboli e gli ID di GUID per tutti i comandi nel pacchetto.  
  
## <a name="vsct-file-design-guidelines"></a>. Linee guida di progettazione File Vsct  
 Per progettare correttamente un file vsct, seguire queste linee guida.  
  
-   Comandi possono essere posizionati solo in gruppi, i gruppi possono essere inseriti solo nei menu e menu possono essere posizionati solo in gruppi. Solo i menu sono effettivamente visualizzati nell'IDE, gruppi e i comandi non lo sono.  
  
-   Sottomenu non possono essere assegnati direttamente a un menu, ma devono essere assegnati a un gruppo, che a sua volta viene assegnato a un menu.  
  
-   I comandi, sottomenu e i gruppi possono essere assegnati a un gruppo padre o menu usando il campo padre della loro definizione direttiva.  
  
-   Organizzazione di una tabella comandi esclusivamente tramite i campi padre nelle direttive di ha un limite significativo. Le direttive che definiscono gli oggetti possono accettare un solo padre argomento.  
  
-   Riutilizzo di comandi, gruppi o sottomenu richiede l'uso di una direttiva di nuovo per creare una nuova istanza dell'oggetto con il proprio `GUID:ID` coppia.  
  
-   Ogni `GUID:ID` coppia deve essere univoca. Riutilizzo di un comando, ad esempio, situato in un menu, una barra degli strumenti o in un menu di scelta rapida viene gestito dal <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.  
  
-   Comandi sia sottomenu possono anche essere assegnati a più gruppi e i gruppi possono essere assegnati a più menu usando la [elemento Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Note sulla File Vsct  
 Se si apportano modifiche a un file con estensione vsct dopo che si sia compilarlo e inserirlo in una DLL satellite nativa, è consigliabile eseguire **devenv.exe /setup /nosetupvstemplates**. Questa operazione forza specificate nel Registro di sistema sperimentale per essere rilettura e il database interno che descrive le risorse di VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] da ricompilare.  
  
 Durante lo sviluppo, è possibile per più progetti VSPackage venga creato e registrato nell'hive del Registro di sistema sperimentale che può provocare confusione confusione nell'IDE. Per risolvere questo problema, è possibile reimpostare l'hive sperimentale per le impostazioni predefinite per rimuovere registrati tutti i pacchetti VSPackage e le eventuali modifiche apportate all'IDE. Per reimpostare l'hive sperimentale, usare lo strumento CreateExpInstance.exe fornito con Visual Studio SDK. È possibile trovarlo in  
  
 **% PROGRAMMI (x86) %\Visual Studio \<versione > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Eseguire lo strumento da riga di comando **CreateExpInstance /Reset**. Tenere presente che questo strumento rimuove da hive sperimentale tutti i pacchetti VSPackage registrati che normalmente non vengono installati con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../../extensibility/extending-menus-and-commands.md)

