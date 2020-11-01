---
title: Impostare i file di simboli (con estensione pdb) e di origine nel debugger
description: Informazioni su come configurare e gestire i file di simboli e di origine in Visual Studio
ms.custom: ''
ms.date: 10/31/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eceffab5b8c179734b1abb5f1005c240912115f1
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2020
ms.locfileid: "89599593"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Specificare i file di simboli (con estensione pdb) e di origine nel debugger di Visual Studio (C#, C++, Visual Basic, F #)

I file del database di programma (con *estensione PDB* ), denominati anche file di simboli, identificatori di mappa e istruzioni nel codice sorgente del progetto per gli identificatori e le istruzioni corrispondenti nelle app compilate. Questi file di mapping collegano il debugger al codice sorgente, che consente il debug.

Quando si compila un progetto dall'IDE di Visual Studio con la configurazione della build di debug standard, il compilatore crea i file di simboli appropriati. Questo articolo descrive come gestire i file di simboli nell'IDE, ad esempio come [specificare il percorso dei simboli nelle opzioni del debugger](#BKMK_Specify_symbol_locations_and_loading_behavior), come [controllare lo stato di caricamento dei simboli](#work-with-symbols-in-the-modules-window) durante il debug e come [impostare le opzioni dei simboli nel codice](#compiler-symbol-options).

Per una spiegazione dettagliata dei file di simboli, vedere gli argomenti seguenti:

- [Informazioni sui file di simboli e le impostazioni dei simboli di Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Perché Visual Studio richiede che i file di simboli del debugger corrispondano esattamente ai file binari con cui sono stati compilati?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Funzionamento dei file di simboli

Il file con *estensione PDB* include informazioni sul debug e sullo stato del progetto che consentono il collegamento incrementale di una configurazione di debug dell'app. Il debugger di Visual Studio USA i file con *estensione PDB* per determinare due informazioni chiave durante il debug:

* Il nome del file di origine e il numero di riga da visualizzare nell'IDE di Visual Studio.
* Posizione in cui arrestare l'app per un punto di interruzione.

I file di simboli mostrano anche il percorso dei file di origine e, facoltativamente, il server da cui recuperarli.

Il debugger carica solo i file con estensione *PDB* che corrispondono esattamente ai file con *estensione PDB* creati al momento della compilazione di un'app, ovvero i file con *estensione PDB* originali o le copie. Questa [duplicazione esatta](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) è necessaria perché il layout delle app può cambiare anche se il codice non è stato modificato.

> [!TIP]
> Per eseguire il debug del codice al di fuori del codice sorgente del progetto, ad esempio il codice di Windows o il codice di terze parti chiamato dal progetto, è necessario specificare il percorso dei file con *estensione PDB* del codice esterno (e, facoltativamente, i file di origine), che devono corrispondere esattamente alle compilazioni nell'app.

## <a name="symbol-file-locations-and-loading-behavior"></a>Percorsi dei file di simboli e comportamento di caricamento

Quando si esegue il debug di un progetto nell'IDE di Visual Studio, il debugger carica automaticamente i file di simboli che si trovano nella cartella del progetto.

> [!NOTE]
> Quando si esegue il debug di codice gestito in un dispositivo remoto, tutti i file di simboli devono trovarsi nel computer locale o in un percorso [specificato nelle opzioni del debugger](#BKMK_Specify_symbol_locations_and_loading_behavior).

Il debugger cerca anche i file di simboli nei percorsi seguenti:

1. Percorso specificato all'interno della DLL o del file eseguibile ( *exe* ).

   Per impostazione predefinita, se è stata compilata una DLL o un file *exe* nel computer in uso, il linker inserisce il percorso completo e il nome del file con *estensione PDB* associato nella dll o nel file *exe* . Il debugger verifica se il file di simboli esiste in tale percorso.

2. La stessa cartella della DLL o del file *exe* .

3. Tutti i percorsi specificati nelle opzioni del debugger per i file di simboli. Per aggiungere e abilitare le posizioni dei simboli, vedere [configurare i percorsi dei simboli e le opzioni di caricamento](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Qualsiasi cartella della cache di simboli locale.

   - Server di simboli e posizioni di rete, Internet o locali specificati, ad esempio i server dei simboli Microsoft, se selezionati. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può scaricare i file di simboli di debug dai server di simboli che implementano il `symsrv` protocollo. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) e gli [strumenti di debug per Windows](/windows-hardware/drivers/debugger/index) sono due strumenti che possono usare i server di simboli.

     I server di simboli che è possibile utilizzare includono:

     **Server di simboli Microsoft pubblici** : per eseguire il debug di un arresto anomalo che si verifica durante una chiamata a una DLL di sistema o a una libreria di terze parti, spesso sono necessari file System *. pdb* . I file System *. pdb* contengono simboli per dll Windows, file *exe* e driver di dispositivo. È possibile ottenere i simboli per i sistemi operativi Windows, MDAC, IIS, ISA e .NET dai server dei simboli Microsoft pubblici.

     **Server di simboli in una rete interna o nel computer locale** : il team o la società può creare server di simboli per i propri prodotti e come cache per i simboli provenienti da origini esterne. Nel computer potrebbe essere presente un server di simboli.

     **Server di simboli di terze parti** : i provider di terze parti delle applicazioni e delle librerie di Windows possono fornire accesso al server di simboli su Internet.

     > [!WARNING]
     > Se si usa un server di simboli diverso dai server di simboli Microsoft pubblici, verificare che il server di simboli e il relativo percorso siano attendibili. Poiché i file di simboli possono contenere codice eseguibile arbitrario, è possibile esporre le minacce alla sicurezza.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Configurare i percorsi dei simboli e le opzioni di caricamento

Nella pagina **strumenti**  >  **Opzioni** di  >  **debug**  >  **simboli** è possibile:

- Specificare e selezionare i percorsi di ricerca e i server di simboli per i componenti Microsoft, Windows o di terze parti.
- Specificare i moduli per i quali si vuole o non si desidera che il debugger carichi automaticamente i simboli.
- Modificare queste impostazioni durante il debug attivo. Vedere [gestire i simboli durante il debug](#manage-symbols-while-debugging).

**Per specificare i percorsi dei simboli e le opzioni di caricamento:**

1. In Visual Studio aprire **strumenti**  >  **Opzioni**  >  **debug**  >  **simboli** (o simboli **Debug**  >  **Opzioni** di debug  >  **Symbols** ).

2. In **percorsi di file di simboli (con estensione pdb)** ,
   - Per usare i server dei simboli **Microsoft** o **NuGet.org** , selezionare la casella di controllo.

   - Per aggiungere un nuovo percorso del server di simboli,
     1. Selezionare il **+** simbolo sulla barra degli strumenti.
     1. Digitare l'URL (http), la condivisione di rete o il percorso locale del server dei simboli o il percorso del simbolo nel campo di testo. La funzione di completamento delle istruzioni facilita l'individuazione del formato corretto.

     ![Strumenti &#45; opzioni &#45; debug &#45; pagina simboli](media/dbg-options-symbols.gif "Strumenti &#45; opzioni &#45; debug &#45; pagina simboli")

     >[!NOTE]
     >Viene eseguita la ricerca solo nella cartella specificata. È necessario aggiungere voci per tutte le sottocartelle in cui si desidera eseguire la ricerca.

   - Per aggiungere un nuovo percorso del server di simboli VSTS,
     1. Selezionare l'icona ![strumenti&#47; opzioni&#47; debug&#47;simboli nuova icona server](media/dbg_tools_options_foldersicon.png "Strumenti &#45; opzioni &#45; debug &#45; icona del nuovo server") sulla barra degli strumenti.
     1. Nella finestra di dialogo **Connetti al server di simboli VSTS** scegliere uno dei server di simboli disponibili e selezionare **Connetti** .

   - Per modificare l'ordine di caricamento per le posizioni dei simboli, usare **CTRL** + **Up** e **CTRL** + **giù** oppure le icone freccia **su** e **giù** .
   - Per modificare un URL o un percorso, fare doppio clic sulla voce oppure selezionarla e premere **F2** .
   - Per rimuovere una voce, selezionarla e quindi selezionare l' **-** icona.

3. Opzionale Per migliorare le prestazioni di caricamento dei simboli, in **memorizza nella cache i simboli in questa directory** , digitare un percorso di cartella locale in cui i server di simboli possono copiare i simboli.

   > [!NOTE]
   > Non inserire la cache dei simboli locale in una cartella protetta, ad esempio C:\Windows o una sottocartella. Usare invece una cartella di lettura e scrittura.

   > [!NOTE]
   > Per i progetti C++, se è `_NT_SYMBOL_PATH` impostata la variabile di ambiente, verrà eseguito l'override del valore impostato in **cache symbols in questa directory** .

4. Specificare i moduli che si desidera vengano caricati dal debugger dal percorso del **file di simboli (con estensione pdb)** all'avvio.

   - Selezionare **carica tutti i moduli, a meno che non sia escluso** (impostazione predefinita) per caricare tutti i simboli per tutti i moduli nel percorso del file di simboli, ad eccezione dei moduli che si escludono in modo specifico. Per escludere determinati moduli, selezionare **specifica moduli esclusi** , selezionare l' **+** icona, digitare i nomi dei moduli da escludere e quindi fare clic su **OK** .

   - Per caricare solo i moduli specificati dai percorsi dei file di simboli, selezionare **carica solo i moduli specificati** . Selezionare **specificare i moduli inclusi** , selezionare l' **+** icona, digitare i nomi dei moduli da includere e quindi fare clic su **OK** . I file di simboli per altri moduli non vengono caricati.

5. Selezionare **OK** .

## <a name="other-symbol-options-for-debugging"></a>Altre opzioni dei simboli per il debug

È possibile selezionare opzioni di simboli aggiuntive in **strumenti**  >  **Opzioni**  >  **debug**  >  **generale** (o opzioni di **debug**  >  **Options**  >  **generale** ):

- **Carica esportazioni DLL (solo nativo)**

  Carica le tabelle di esportazione DLL per C/C++. Per informazioni dettagliate, vedere le [tabelle di esportazione DLL](#use-dumpbin-exports). La lettura delle informazioni di esportazione della DLL comporta un sovraccarico, quindi il caricamento delle tabelle di esportazione è disattivato per impostazione predefinita. È anche possibile usare `dumpbin /exports` in una riga di comando di compilazione C/C++.

- **Abilita debug a livello di indirizzo** e **Mostra disassembly se l'origine non è disponibile**

  Mostra sempre il disassembly quando i file di origine o di simboli non vengono trovati.

  ![Opzioni &#47; debug &#47; opzioni generali del Disassembly](../debugger/media/dbg_options_general_disassembly_checkbox.png "Opzioni &#47; debug &#47; opzioni generali del Disassembly")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Abilita supporto del server di origine**

  Usa il server di origine per facilitare il debug di un'app quando non è presente codice sorgente nel computer locale oppure il file con *estensione PDB* non corrisponde al codice sorgente. Il server di origine accetta richieste di file e restituisce i file effettivi dal controllo del codice sorgente. Il server di origine viene eseguito utilizzando una DLL denominata *srcsrv.dll* per leggere il file con *estensione PDB* dell'app. Il file con *estensione PDB* contiene i puntatori al repository del codice sorgente, nonché i comandi utilizzati per recuperare il codice sorgente dal repository.

  È possibile limitare i comandi che *srcsrv.dll* possibile eseguire dal file *PDB* dell'app elencando i comandi consentiti in un file denominato *srcsrv.ini* . Inserire il file di *srcsrv.ini* nella stessa cartella *srcsrv.dll* e *devenv.exe* .

  >[!IMPORTANT]
  >I comandi arbitrari possono essere incorporati nel file con *estensione PDB* di un'app, quindi assicurarsi di inserire solo i comandi da eseguire in un file di *srcsrv.ini* . Eventuali tentativi di eseguire un comando non presente nel file *srcsvr.ini* causerà la visualizzazione di una finestra di dialogo di conferma. Per altre informazioni, vedere [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Poiché non viene eseguita alcuna convalida sui parametri dei comandi, prestare attenzione nell'utilizzare i comandi attendibili. Se, ad esempio, è stato elencato *cmd.exe* nel *srcsrv.ini* , un utente malintenzionato potrebbe specificare parametri in *cmd.exe* che lo renderebbe pericoloso.

  Selezionare questo elemento e gli elementi figlio desiderati. **Consenti al server di origine per gli assembly parzialmente attendibili (solo gestito)** ed **Esegui sempre comandi del server di origine non attendibili senza chiedere conferma** possono aumentare i rischi per la sicurezza.

  ![Opzioni di abilitazione del server di origine](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Opzioni simboli del compilatore

Quando si compila un progetto dall'IDE di Visual Studio con la configurazione della build di **debug** standard, i compilatori C++ e gestiti creano i file di simboli appropriati per il codice. È anche possibile impostare le opzioni del compilatore nel codice.

### <a name="net-options"></a>Opzioni .NET

Compilare con **/debug** per creare un file con *estensione PDB* . È possibile compilare applicazioni con **/debug:full** o **/debug:pdbonly** . Se si usa l'opzione di compilazione **/debug:full** , verrà generato codice di cui è possibile effettuare il debug. Se si usa l'opzione di compilazione **/debug:pdbonly** , vengono generati file con estensione *pdb* ma non l'attributo `DebuggableAttribute` che indica al compilatore JIT che sono disponibili informazioni di debug. Usare **/debug:pdbonly** per generare file con estensione *pdb* per una build di rilascio che non si vuole sottoporre a debug. Per ulteriori informazioni, vedere [/debug (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) o [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>Opzioni C/C++

- File *VC \<x> . pdb* e *\<project> . pdb*

  Quando si esegue la compilazione con [/Zi o/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format), viene creato un file con *estensione PDB* per C/C++. In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] , l'opzione [/FD](/cpp/build/reference/fd-program-database-file-name) assegna un nome al file con *estensione PDB* creato dal compilatore. Quando si crea un progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzando l'IDE, l'opzione **/FD** viene impostata in modo da creare un file con *estensione PDB* denominato *\<project> PDB* .

  Se si compila l'applicazione C/C++ usando un makefile e si specifica **/Zi** o **/Zi** senza usare **/FD** , il compilatore crea due file con *estensione PDB* :

  - *VC \<x> . pdb* , dove *\<x>* rappresenta la versione del compilatore Microsoft C++, ad esempio *VC11. pdb*

    Il file *VC \<x> . pdb* archivia tutte le informazioni di debug per i singoli file oggetto e si trova nella stessa directory del makefile del progetto. Ogni volta che viene creato un file oggetto, il compilatore C/C++ unisce le informazioni di debug nel file *VC \<x> . pdb* . Quindi, anche se ogni file di origine include file di intestazione comuni, ad esempio *\<windows.h>* , i typedef di tali intestazioni vengono archiviati una sola volta, anziché in ogni file oggetto. Queste includono informazioni sui tipi ma non sui simboli, ad esempio sulle definizioni delle funzioni.

  - *\<project>PDB*

    Il file con *\<project> estensione PDB* archivia tutte le informazioni di debug per il file *exe* del progetto e risiede nella sottodirectory *\Debug* Il file con *\<project> estensione PDB* contiene informazioni complete sul debug, inclusi i prototipi di funzione, non solo le informazioni sul tipo disponibili in *VC \<x> . pdb* .

  Entrambi i file *VC \<x> . pdb* e *\<project> . pdb* consentono gli aggiornamenti incrementali. Il linker incorpora anche il percorso dei file con *estensione PDB* nel file con estensione *exe* o *dll* creato.

- <a name="use-dumpbin-exports"></a>Tabelle di esportazione DLL

  Usare `dumpbin /exports` per visualizzare i simboli disponibili nella tabella di esportazione di una dll. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili per l'utilizzo di messaggi di Windows, procedure di Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco.

  Leggendo l' `dumpbin /exports` output, è possibile visualizzare i nomi esatti delle funzioni, compresi i caratteri non alfanumerici. La visualizzazione dei nomi di funzione esatti è utile per impostare un punto di interruzione in una funzione, perché i nomi di funzione possono essere troncati altrove nel debugger. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Applicazioni Web

Impostare la modalità di debug per il file di *web.config* dell'applicazione ASP.NET. Tramite la modalità di debug, ASP.NET genera simboli per i file generati dinamicamente e il debugger si collega all'applicazione ASP.NET. Visual Studio imposta questa impostazione automaticamente quando si avvia il debug, se il progetto è stato creato dal modello dei progetti Web.

## <a name="manage-symbols-while-debugging"></a>Gestire i simboli durante il debug

È possibile usare **moduli** , **stack di chiamate** , **variabili locali** , **auto** o qualsiasi finestra espressioni di **controllo** per caricare simboli o modificare le opzioni dei simboli durante il debug. Per altre informazioni, vedere [acquisire familiarità con la modalità di connessione del debugger all'app](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="work-with-symbols-in-the-modules-window"></a>Usare i simboli nella finestra moduli

Durante il debug, nella finestra **moduli** vengono visualizzati i moduli di codice che il debugger tratta come codice utente, il codice e il relativo stato di caricamento dei simboli. È anche possibile monitorare lo stato di caricamento dei simboli, caricare i simboli e modificare le opzioni dei simboli nella finestra **moduli** .

**Per monitorare o modificare le posizioni o le opzioni di simboli durante il debug:**

1. Per aprire la finestra **moduli** , durante il debug selezionare **debug**  >  **Windows**  >  **moduli** di Windows.
1. Nella finestra **moduli** fare clic con il pulsante destro del mouse sullo **stato dei simboli** o sulle intestazioni dei **file di simboli** o su qualsiasi modulo.
1. Dal menu di scelta rapida scegliere una delle opzioni seguenti:

|Opzione|Descrizione|
|------------|-----------------|
|**Carica simboli**|Viene visualizzato per i moduli con simboli ignorati, non trovati o non caricati. Tenta di caricare i simboli dai percorsi specificati nella pagina **Opzioni** di  >  **debug** dei  >  **simboli** . Se il file di simboli non è stato trovato o non è stato caricato, avvia **Esplora file** in modo da poter specificare un nuovo percorso per la ricerca.|
|**Informazioni sul caricamento simboli**|Mostra la posizione di un file di simboli caricato o i percorsi cercati se il file non è stato trovato dal debugger.|
|**Impostazioni simboli**|Apre la pagina **Opzioni** di  >  **debug**  >  **simboli** , in cui è possibile modificare e aggiungere posizioni dei simboli.|
|**Caricare sempre automaticamente**|Aggiunge il file di simboli selezionato all'elenco di file caricati automaticamente dal debugger.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Usare le pagine nessun simbolo caricato/nessuna origine caricata

Esistono diversi modi in cui il debugger può suddividere il codice in cui non sono disponibili file di simboli o di origine:

- Eseguire un'istruzione nel codice.
- Interrompere il codice da un punto di interruzione o un'eccezione.
- Passa a un thread diverso.
- Modificare il stack frame facendo doppio clic su un frame nella finestra **stack di chiamate** .

Quando si verifica questa situazione, il debugger Visualizza i **simboli non caricati** o **Nessuna pagina caricata dall'origine** per facilitare l'individuazione e il caricamento dei simboli o dell'origine necessari.

 ![Pagina Nessun simbolo caricato](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Per utilizzare la pagina del documento nessun simbolo caricato per individuare e caricare i simboli mancanti:**

- Per modificare il percorso di ricerca, selezionare un percorso non selezionato oppure selezionare **nuovo percorso** o **nuovo percorso VSTS** e immettere o selezionare un nuovo percorso. Selezionare **carica** per cercare nuovamente i percorsi e caricare il file di simboli se viene trovato.
- Per eseguire l'override di tutte le opzioni dei simboli e ripetere i percorsi di ricerca, selezionare **Sfoglia e trova \<executable-name>** . Il file di simboli viene caricato se viene trovato oppure **Esplora file** consente di selezionare manualmente il file di simboli.
- Per aprire la pagina **Opzioni** di  >  **debug**  >  **simboli** , selezionare **Modifica impostazioni simboli** .
- Per visualizzare il disassembly in una nuova finestra una volta, selezionare **Visualizza Disassembly** oppure selezionare la finestra di **dialogo Opzioni** per impostare l'opzione in modo che mostri sempre il disassembly quando i file di origine o di simboli non vengono trovati.
- Per visualizzare i percorsi cercati e il risultato, espandere **informazioni sul caricamento dei simboli** .

Se il debugger trova il file con *estensione PDB* dopo l'esecuzione di una delle opzioni e può recuperare il file di origine utilizzando le informazioni nel file con *estensione PDB* , viene visualizzata l'origine. In caso contrario, viene visualizzata una pagina **Nessuna origine caricata** in cui viene descritto il problema, con collegamenti a azioni che potrebbero risolvere il problema.

**Per aggiungere i percorsi di ricerca dei file di origine a una soluzione:**

È possibile specificare i percorsi in cui il debugger cerca i file di origine ed esclude i file specifici dalla ricerca.

1. Selezionare la soluzione in **Esplora soluzioni** , quindi selezionare l'icona **Proprietà** , premere **ALT** + **invio** oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà** .

1. Selezionare **Esegui debug dei file di origine** .

1. In **directory che contengono codice sorgente** Digitare o selezionare i percorsi di codice sorgente in cui eseguire la ricerca. Usare l'icona **nuova riga** per aggiungere altre posizioni, le icone freccia **su** e **giù** per riordinarle o l'icona **X** per eliminarle.

   >[!NOTE]
   >Il debugger esegue la ricerca solo nella directory specificata. È necessario aggiungere voci per qualsiasi sottodirectory da cercare.

1. In non **cercare questi file di origine** , digitare i nomi dei file di origine da escludere dalla ricerca.

1. Selezionare **OK** o **applica** .

## <a name="see-also"></a>Vedere anche
- [Informazioni sui file di simboli e le impostazioni dei simboli di Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Modifiche al caricamento remoto dei simboli .NET in Visual Studio 2012 e 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)