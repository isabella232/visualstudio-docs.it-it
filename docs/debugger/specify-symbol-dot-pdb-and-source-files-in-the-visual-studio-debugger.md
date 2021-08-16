---
title: Impostare i file di simboli (con estensione pdb) e di origine nel debugger
description: Informazioni su come configurare e gestire i file di simboli e di origine in Visual Studio
ms.custom: ''
ms.date: 3/31/2021
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 76e12b710a72c5ccf97776bf5b7fb4964ba56c1faa1b4b094231244f2ddb431c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361887"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Specificare i file di simboli (con estensione pdb) e di origine nel debugger Visual Studio (C#, C++, Visual Basic, F#)

File di database di programma (con estensione *pdb),* detti anche file di simboli, identificatori di mapping e istruzioni nel codice sorgente del progetto agli identificatori e alle istruzioni corrispondenti nelle app compilate. Questi file di mapping collegano il debugger al codice sorgente, che consente il debug.

Quando si compila un progetto dall'IDE Visual Studio con la configurazione della build di debug standard, il compilatore crea i file di simboli appropriati. Questo articolo descrive come gestire i file di simboli nell'IDE, ad esempio come specificare [](#work-with-symbols-in-the-modules-window) il percorso dei simboli nelle opzioni del [debugger,](#BKMK_Specify_symbol_locations_and_loading_behavior)come controllare lo stato di caricamento dei simboli durante il debug e come impostare le opzioni dei simboli nel [codice.](#compiler-symbol-options)

Per una spiegazione dettagliata dei file di simboli, vedere quanto segue:

- [Informazioni sui file di simboli e Visual Studio delle simboli](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Perché Visual Studio file di simboli del debugger in modo che corrispondano esattamente ai file binari con cui sono stati compilati?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Funzionamento dei file di simboli

Il file *con estensione pdb* contiene informazioni sul debug e sullo stato del progetto che consentono il collegamento incrementale di una configurazione di debug dell'app. Il debugger Visual Studio usa *i file con estensione pdb* per determinare due informazioni chiave durante il debug:

* Nome del file di origine e numero di riga da visualizzare nell Visual Studio IDE.
* Posizione in cui arrestare l'app per un punto di interruzione.

I file di simboli mostrano anche il percorso dei file di origine e, facoltativamente, il server da cui recuperarli.

Il debugger carica solo i file con estensione *pdb* che corrispondono esattamente ai file con estensione *pdb* creati durante la creazione di un'app, ovvero i file *con estensione pdb* originali o le copie. Questa [duplicazione esatta](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) è necessaria perché il layout delle app può cambiare anche se il codice stesso non è stato modificato.

> [!TIP]
> Per eseguire il debug di codice all'esterno del codice sorgente del progetto, ad esempio codice Windows o codice di terze parti chiamato dal progetto, è necessario specificare il percorso dei file con estensione *pdb* del codice esterno (e, facoltativamente, i file di origine), che devono corrispondere esattamente alle compilazioni nell'app.

## <a name="symbol-file-locations-and-loading-behavior"></a>Percorsi dei file di simboli e comportamento di caricamento

Quando si esegue il debug di un progetto nell'IDE Visual Studio, il debugger carica automaticamente i file di simboli che si trovano nella cartella del progetto.

> [!NOTE]
> Quando si esegue il debug di codice gestito in un dispositivo remoto, tutti i file di simboli devono trovarsi nel computer locale o in un percorso specificato [nelle opzioni del debugger](#BKMK_Specify_symbol_locations_and_loading_behavior).

Il debugger cerca anche i file di simboli nei percorsi seguenti:

1. Percorso specificato all'interno della DLL o del file eseguibile (*.exe*) .

   Per impostazione predefinita, se nel computer è stata compilata una DLL o un file *.exe,* il linker inserisce il percorso completo e il nome file del file con estensione *pdb* associato nella DLL o nel file *.exe.* Il debugger verifica se il file di simboli esiste in tale percorso.

2. Stessa cartella della DLL o del file *.exe* file.

3. Tutti i percorsi specificati nelle opzioni del debugger per i file di simboli. Per aggiungere e abilitare le posizioni dei simboli, vedere [Configurare i percorsi dei simboli e le opzioni di caricamento.](#BKMK_Specify_symbol_locations_and_loading_behavior)

   - Qualsiasi cartella della cache di simboli locale.

   - Percorsi e server di simboli di rete, Internet o locali specificati, ad esempio i server di simboli Microsoft, se selezionati. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può scaricare i file di simboli di debug dai server di simboli che implementano il `symsrv` protocollo . [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) e gli [strumenti di debug per Windows](/windows-hardware/drivers/debugger/index) sono due strumenti che possono usare i server di simboli.

     I server di simboli che è possibile usare includono:

     **Server di simboli Microsoft pubblici:** per eseguire il debug di un arresto anomalo che si verifica durante una chiamata a una DLL di sistema o a una libreria di terze parti, spesso sono necessari file *con estensione pdb di* sistema. I *file con estensione pdb* di sistema contengono simboli Windows DLL, *.exe* file e driver di dispositivo. È possibile ottenere simboli per Windows, MDAC, IIS, ISA e .NET dai server di simboli Microsoft pubblici.

     **Server di simboli in una rete interna** o nel computer locale: il team o l'azienda può creare server di simboli per i propri prodotti e come cache per i simboli da origini esterne. Nel computer potrebbe essere presente un server di simboli.

     **Server di simboli di terze parti:** i provider di servizi di Windows e le librerie possono fornire l'accesso al server di simboli su Internet.

     > [!WARNING]
     > Se si usa un server di simboli diverso dai server di simboli Microsoft pubblici, assicurarsi che il server dei simboli e il relativo percorso siano attendibili. Poiché i file di simboli possono contenere codice eseguibile arbitrario, è possibile essere esposti a minacce per la sicurezza.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Configurare i percorsi dei simboli e le opzioni di caricamento

Nella pagina **Strumenti**  >  **Opzioni**  >  **Simboli**  >  **di** debug è possibile:

- Specificare e selezionare percorsi di ricerca e server di simboli per microsoft, Windows o componenti di terze parti.
- Specificare i moduli per i quali il debugger deve caricare automaticamente i simboli.
- Modificare queste impostazioni durante il debug attivo. Vedere Gestire [i simboli durante il debug.](#manage-symbols-while-debugging)

**Per specificare i percorsi dei simboli e le opzioni di caricamento:**

1. In Visual Studio strumenti **Opzioni** Simboli di  >  **debug**  >    >   (o Simboli delle **opzioni**  >    >  **di debug**).

2. In **Percorsi file di simboli (con estensione pdb)**,
   - Per usare **i server di simboli Microsoft** o **NuGet.org Symbol Server,** selezionare la casella di controllo.

   - Per aggiungere un nuovo percorso del server dei simboli,
     1. Selezionare il **+** simbolo nella barra degli strumenti.
     1. Digitare l'URL (http), la condivisione di rete o il percorso locale del server di simboli o del percorso dei simboli nel campo di testo. La funzione di completamento delle istruzioni facilita l'individuazione del formato corretto.

     ![Strumenti &#45; opzioni &#45; debug &#45; simboli](media/dbg-options-symbols.gif "Strumenti &#45; opzioni &#45; debug &#45; simboli")

     >[!NOTE]
     >Viene cercata solo la cartella specificata. È necessario aggiungere voci per le sottocartelle in cui si desidera eseguire la ricerca.

   - Per aggiungere un nuovo percorso del server di simboli VSTS,
     1. Selezionare Strumenti ![e&#47; opzioni&#47; debug&#47;'icona](media/dbg_tools_options_foldersicon.png "Strumenti &#45; opzioni &#45; debug &#45; Simboli nuovo server") del server Simboli nuova icona del server sulla barra degli strumenti.
     1. Nella finestra **Connessione al server di simboli VSTS** scegliere uno dei server di simboli disponibili e selezionare **Connessione**.

   - Per modificare l'ordine di caricamento per le posizioni dei simboli, usare **CTRL** SU e CTRL GIÙ oppure le icone freccia SU +   +  **e** GIÙ. 
   - Per modificare un URL o un percorso, fare doppio clic sulla voce o selezionarla e premere **F2.**
   - Per rimuovere una voce, selezionarla e quindi selezionare **-** l'icona.

3. (Facoltativo) Per migliorare le prestazioni di caricamento dei simboli, **in Memorizza nella cache** i simboli in questa directory digitare il percorso di una cartella locale in cui i server di simboli possono copiare i simboli.

   > [!NOTE]
   > Non inserire la cache dei simboli locale in una cartella protetta, ad esempio C:\Windows o una sottocartella. Usare invece una cartella di lettura e scrittura.

   > [!NOTE]
   > Per i progetti C++, se la variabile di ambiente è impostata, eseguirà l'override del valore impostato in Memorizza nella `_NT_SYMBOL_PATH` cache i simboli in questa **directory**.

4. Specificare i moduli che il debugger deve caricare dai percorsi dei file di simboli (con estensione **pdb)** all'avvio.

   - Selezionare **Carica tutti i moduli,** a meno che non sia escluso (impostazione predefinita) per caricare tutti i simboli per tutti i moduli nel percorso del file di simboli, ad eccezione dei moduli esclusi in modo specifico. Per escludere determinati moduli, selezionare Specifica **moduli** esclusi, selezionare l'icona, digitare i nomi dei moduli da **+** escludere e selezionare **OK.**

   - Per caricare solo i moduli specificati dai percorsi dei file di simboli, **selezionare Carica solo i moduli specificati.** Selezionare **Specifica moduli inclusi,** selezionare **+** l'icona, digitare i nomi dei moduli da includere e quindi selezionare **OK.** I file di simboli per altri moduli non vengono caricati.

5. Selezionare **OK**.

## <a name="other-symbol-options-for-debugging"></a>Altre opzioni di simboli per il debug

È possibile selezionare opzioni aggiuntive per i simboli **in** Strumenti  >  **Opzioni**  >  **Debug**  >  **Generale** (o **Opzioni di debug**  >    >  **Generale):**

- **Caricare esportazioni DLL (solo native)**

  Carica le tabelle di esportazione DLL per C/C++. Per informazioni dettagliate, vedere [Tabelle di esportazione DLL.](#use-dumpbin-exports) La lettura delle informazioni di esportazione dll comporta un sovraccarico, pertanto il caricamento delle tabelle di esportazione è disattivato per impostazione predefinita. È anche possibile usare in una riga di comando di `dumpbin /exports` compilazione C/C++.

- **Abilitare il debug a livello di indirizzo** e Mostra **disassembly se l'origine non è disponibile**

  Visualizza sempre il disassembly quando i file di origine o di simboli non vengono trovati.

  ![Opzioni &#47; debug &#47; opzioni generali disassembly](../debugger/media/dbg_options_general_disassembly_checkbox.png "Opzioni &#47; debug &#47; opzioni disassembly generale")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Abilitare il supporto del server di origine**

  Usa il server di origine per eseguire il debug di un'app quando non è presente codice sorgente nel computer locale o il file con estensione *pdb* non corrisponde al codice sorgente. Il server di origine accetta le richieste di file e restituisce i file effettivi dal controllo del codice sorgente. Il server di origine viene eseguito usando una DLL *srcsrv.dll* per leggere il file *con estensione pdb* dell'app. Il file *con estensione pdb* contiene puntatori al repository del codice sorgente, nonché comandi usati per recuperare il codice sorgente dal repository.

  È possibile limitare i comandi *chesrcsrv.dll* possono essere eseguiti dal file con estensione *pdb* dell'app elencando i comandi consentiti in un file *denominatosrcsrv.ini*. Posizionare il *srcsrv.ini* file nella stessa cartella di *srcsrv.dll* e *devenv.exe*.

  >[!IMPORTANT]
  >I comandi arbitrari possono essere incorporati nel file con estensione *pdb* di un'app, quindi assicurarsi di inserire solo i comandi da eseguire in un file *srcsrv.ini* file. Eventuali tentativi di eseguire un comando non presente nel file *srcsvr.ini* causerà la visualizzazione di una finestra di dialogo di conferma. Per altre informazioni, vedere [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Poiché non viene eseguita alcuna convalida sui parametri dei comandi, prestare attenzione nell'utilizzare i comandi attendibili. Se, ad esempio,cmd.exeelencati nel *srcsrv.ini*, un utente  malintenzionato potrebbe specificare parametricmd.exeche lo renderebbero pericoloso. 

  Selezionare questo elemento e gli elementi figlio desiderati. Consentire al server di origine di assembly parzialmente attendibili **(solo gestito)** ed eseguire sempre comandi **del server** di origine non attendibili senza chiedere conferma può aumentare i rischi per la sicurezza.

  ![Opzioni di abilitazione del server di origine](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Opzioni dei simboli del compilatore

Quando si compila un progetto dall'IDE Visual Studio con la configurazione di compilazione debug **standard,** i compilatori C++ e gestiti creano i file di simboli appropriati per il codice. È anche possibile impostare le opzioni del compilatore nel codice.

### <a name="net-options"></a>Opzioni .NET

Compilare **con /debug** per creare un file *con estensione pdb.* È possibile compilare applicazioni con **/debug:full** o **/debug:pdbonly**. Se si usa l'opzione di compilazione **/debug:full** , verrà generato codice di cui è possibile effettuare il debug. Se si usa l'opzione di compilazione **/debug:pdbonly**, vengono generati file con estensione *pdb* ma non l'attributo `DebuggableAttribute` che indica al compilatore JIT che sono disponibili informazioni di debug. Usare **/debug:pdbonly** per generare file con estensione *pdb* per una build di rilascio che non si vuole sottoporre a debug. Per altre informazioni, vedere [/debug (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) o [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>Opzioni C/C++

- *File \<x> con estensione pdb* e *\<project> pdb di* VC

  Quando si compila con /ZI o [/Zi,](/cpp/build/reference/z7-zi-zi-debug-information-format)viene creato un file con estensione *pdb* per C/C++. In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] [l'opzione /Fd](/cpp/build/reference/fd-program-database-file-name) imposta il nome del file *con estensione pdb* creato dal compilatore. Quando si crea un progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando l'IDE, **l'opzione /Fd** viene impostata per creare un file *con estensione pdb* denominato *\<project> pdb*.

  Se si compila l'applicazione C/C++ usando un makefile e si specifica **/ZI** o **/Zi** senza **usare /Fd,** il compilatore crea due *file con estensione pdb:*

  - *VC \<x> .pdb*, dove *\<x>* rappresenta la versione del compilatore Microsoft C++, ad esempio *VC11.pdb*

    Il file *\<x> con estensione pdb* di VC archivia tutte le informazioni di debug per i singoli file oggetto e si trova nella stessa directory del makefile del progetto. Ogni volta che crea un file oggetto, il compilatore C/C++ unisce le informazioni di debug in *VC \<x> .pdb.* Pertanto, anche se ogni file di origine include file di intestazione comuni, ad esempio , i typedef di tali intestazioni vengono archiviati una sola *\<windows.h>* volta, anziché in ogni file oggetto. Queste includono informazioni sui tipi ma non sui simboli, ad esempio sulle definizioni delle funzioni.

  - *\<project>Pdb*

    Il file *\<project> con estensione pdb* archivia tutte le informazioni di debug per il file *.exe* del progetto e si trova nella *sottodirectory \debug.* Il file *\<project> con estensione pdb* contiene informazioni di debug complete, inclusi i prototipi di funzione, non solo le informazioni sul tipo disponibili in *VC \<x> .pdb.*

  Entrambi i *file \<x> con estensione pdb* e *\<project> pdb* di VC consentono gli aggiornamenti incrementali. Il linker incorpora anche il percorso dei file  con estensione *pdb* nel.exeo.dll *file* creato.

- <a name="use-dumpbin-exports"></a>Tabelle di esportazione DLL

  Usare `dumpbin /exports` per visualizzare i simboli disponibili nella tabella di esportazione di una DLL. Le informazioni simboliche delle tabelle di esportazione dll possono essere utili per l'uso di messaggi Windows, procedure Windows (WindowProcs), oggetti COM, marshalling o qualsiasi DLL per cui non si dispone di simboli. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco.

  Leggendo `dumpbin /exports` l'output, è possibile visualizzare i nomi esatti delle funzioni, inclusi i caratteri non alfanumerici. La visualizzazione dei nomi esatti delle funzioni è utile per impostare un punto di interruzione in una funzione, perché i nomi delle funzioni possono essere troncati altrove nel debugger. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Applicazioni Web

Impostare il *web.config* file dell'applicazione ASP.NET in modalità di debug. Tramite la modalità di debug, ASP.NET genera simboli per i file generati dinamicamente e il debugger si collega all'applicazione ASP.NET. Visual Studio imposta automaticamente questa impostazione quando si avvia il debug, se il progetto è stato creato dal modello di progetti Web.

## <a name="manage-symbols-while-debugging"></a>Gestire i simboli durante il debug

È possibile usare moduli , Stack di **chiamate**,  **Variabili** locali , **Auto o** qualsiasi finestra Espressioni di controllo per caricare simboli o modificare le opzioni dei simboli durante il debug.  Per altre informazioni, vedere Acquisire familiarità con il [modo in cui il debugger si connette all'app.](../debugger/debugger-tips-and-tricks.md#modules_window)

### <a name="work-with-symbols-in-the-modules-window"></a>Usare i simboli nella finestra Moduli

Durante il debug, la **finestra Moduli** mostra i moduli di codice trattati dal debugger come codice utente o My Code e il relativo stato di caricamento dei simboli. È anche possibile monitorare lo stato di caricamento dei simboli, caricare i simboli e modificare le opzioni dei simboli nella **finestra** Moduli.

**Per monitorare o modificare le posizioni o le opzioni dei simboli durante il debug:**

1. Per aprire la **finestra Moduli,** durante il debug, selezionare   >  **Debug Windows**  >  **moduli** (o premere **CTRL**  +    +  **ALT+U).**
1. Nella finestra **Moduli fare** clic con il pulsante destro del mouse **sull'intestazione Stato** simbolo o **File** di simboli o su qualsiasi modulo.
1. Dal menu di scelta rapida scegliere una delle opzioni seguenti:

|Opzione|Descrizione|
|------------|-----------------|
|**Carica simboli**|Viene visualizzato per i moduli con simboli ignorati, non trovati o non caricati. Tenta di caricare i simboli dai percorsi specificati nella pagina **Simboli**  >  **di**  >  **debug** delle opzioni. Se il file di simboli non viene trovato o non caricato, avvia Esplora file **in** modo da poter specificare un nuovo percorso in cui eseguire la ricerca.|
|**Informazioni sul caricamento simboli**|Visualizza il percorso di un file di simboli caricato o i percorsi in cui è stata cercata se il debugger non riesce a trovare il file.|
|**Simbolo Impostazioni**|Apre la **pagina Simboli**  >  **di debug** delle  >   opzioni, in cui è possibile modificare e aggiungere i percorsi dei simboli.|
|**Caricare sempre automaticamente**|Aggiunge il file di simboli selezionato all'elenco di file caricati automaticamente dal debugger.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Usare le pagine Nessun simbolo caricato/Nessuna origine caricata

Esistono diversi modi per interrompere l'esecuzione del debugger nel codice in cui non sono disponibili file di simboli o di origine:

- Eseguire un'istruzione al codice.
- Interrompere il codice da un punto di interruzione o un'eccezione.
- Passare a un thread diverso.
- Modificare il stack frame facendo doppio clic su un frame nella finestra **Stack di** chiamate.

In questo caso, il  debugger visualizza le pagine Nessun simbolo caricato o Nessuna origine **caricata** per individuare e caricare i simboli o l'origine necessari.

 ![Pagina Nessun simbolo caricato](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Per usare la pagina del documento Nessun simbolo caricato per trovare e caricare i simboli mancanti:**

- Per modificare il percorso di ricerca, selezionare  un percorso non selezionato oppure selezionare Nuovo percorso o Nuovo percorso **VSTS** e immettere o selezionare un nuovo percorso. Selezionare **Carica** per cercare di nuovo i percorsi e caricare il file di simboli, se presente.
- Per eseguire l'override delle opzioni dei simboli e ripetere i percorsi di ricerca, **selezionare Sfoglia e trovare \<executable-name>**. Il file di simboli viene caricato se viene trovato o Esplora file **viene** aperto in modo da poter selezionare manualmente il file di simboli.
- Per aprire la pagina delle impostazioni dei simboli per configurare il comportamento, selezionare Cambia **simbolo Impostazioni** (o scegliere **Opzioni** Simboli  >  **di**  >  **debug**).
- (Avanzate) Per visualizzare il disassembly in una nuova finestra una sola  volta, selezionare visualizza **disassembly** oppure selezionare la finestra di dialogo Opzioni per impostare l'opzione per visualizzare sempre il disassembly quando non vengono trovati file di origine o simboli. Per altre informazioni, vedere [Visualizzare il codice disassembly](../debugger/how-to-use-the-disassembly-window.md).
- Per visualizzare i percorsi cercati e il risultato, espandere **Informazioni sul caricamento dei simboli**.
- Per il codice C#, è anche possibile scegliere  di [decompilare](../debugger/decompilation.md) il codice sorgente dalle pagine Nessun simbolo caricato o **Nessuna origine caricata.**

Se il debugger trova il file con estensione *pdb* dopo aver eseguito una delle opzioni e può recuperare il file di origine usando le informazioni nel file *con estensione pdb,* visualizza l'origine. In caso contrario, viene visualizzata una pagina Nessuna origine **caricata** che descrive il problema, con collegamenti ad azioni che potrebbero risolvere il problema.

**Per aggiungere percorsi di ricerca di file di origine a una soluzione:**

È possibile specificare i percorsi in cui il debugger cerca i file di origine ed escludere file specifici dalla ricerca.

1. Selezionare la soluzione in **Esplora soluzioni** e quindi selezionare **l'icona** Proprietà, premere **ALT INVIO** oppure fare clic con il pulsante destro del mouse + e **scegliere Proprietà**.

1. Selezionare **Debug file di origine**.

   ![Pagina Esegui debug dei file di origine](../debugger/media/dbg-source-files.png)

1. In **Directory contenenti codice sorgente** digitare o selezionare i percorsi del codice sorgente in cui eseguire la ricerca. Usare **l'icona Nuova** riga per  aggiungere  altre posizioni, le icone freccia Su e Giù per riordinarle o l'icona **X** per eliminarle.

   >[!NOTE]
   >Il debugger cerca solo la directory specificata. È necessario aggiungere voci per qualsiasi sottodirectory da cercare.

1. In **Non cercare questi file di origine** digitare i nomi dei file di origine da escludere dalla ricerca.

1. Selezionare **OK** o **Applica**.

## <a name="see-also"></a>Vedi anche
- [Informazioni sui file di simboli Visual Studio le impostazioni dei simboli](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Modifiche di caricamento dei simboli remoti .NET in Visual Studio 2012 e 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)