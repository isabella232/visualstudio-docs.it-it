---
title: Specifica simboli (PDB) e i file di origine nel debugger di | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/05/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c289da63a8fbc8469734e905c29edca1149e04c4
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257381"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Specifica simboli (PDB) e i file di origine nel debugger di Visual Studio (C#, C++, Visual Basic, F#)

Database di programma (*PDB*) i file, chiamati anche file di simboli, eseguire il mapping di identificatori e le istruzioni nel codice sorgente del progetto per gli identificatori corrispondenti e le istruzioni in compilate le app. 

Quando si compila un progetto dall'IDE di Visual Studio con lo standard di configurazione della build di Debug, il compilatore crea i file di simboli appropriati. È anche possibile [impostare le opzioni dei simboli nel codice](#compiler-symbol-options). 

Il *PDB* file contiene le informazioni sullo stato di progetto e di debug che consentono il collegamento incrementale di una configurazione di Debug dell'app. Il debugger di Visual Studio Usa *PDB* file per determinare i due tipi principali di informazioni durante il debug:

* Il file di origine nome e la riga numero da visualizzare nell'IDE di Visual Studio.
* Posizione in cui nell'app per arrestare un punto di interruzione.

I file di simboli mostrano anche il percorso del file di origine e, facoltativamente, per recuperarli dal server.
  
Il debugger carica solo *PDB* i file che corrispondono esattamente al *PDB* file creati quando è stata compilata un'app (originale, ovvero *PDB* copie o file). Questa duplicazione esatta è necessaria perché il layout delle App può cambiare anche se il codice non è stato modificato. Per altre informazioni, vedere [perché Visual Studio richiede file di simboli del debugger una corrispondenza esatta tra i file binari con cui sono stati creati?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

> [!TIP]
> Per eseguire il debug di codice di fuori del codice sorgente del progetto, ad esempio codice Windows o terze parti chiamato dal progetto di codice, è necessario specificare il percorso al codice esterno *PDB* file (e, facoltativamente, i file di origine), che deve corrispondere esattamente a le compilazioni nell'app. 

## <a name="symbol-file-locations-and-loading-behavior"></a>Percorsi dei file e il comportamento del caricamento dei simboli

> [!NOTE]
> Durante il debug di codice gestito in un dispositivo remoto, tutti i file di simboli devono trovarsi nel computer locale o in un luogo [specificati nelle opzioni del debugger](#BKMK_Specify_symbol_locations_and_loading_behavior).  
  
Quando si esegue il debug di un progetto nell'IDE di Visual Studio, il debugger carica automaticamente i file di simboli che si trovano nella cartella del progetto. 

Inoltre, il debugger cerca i file di simboli nei percorsi seguenti:

1. Il percorso specificato nella DLL o del file eseguibile (*.exe*) file.  
   
   Per impostazione predefinita, se è stata compilata una DLL o un *.exe* file nel computer, il linker inserisce il percorso completo e il nome dell'oggetto associato *PDB* file nella DLL o *.exe* file. Il debugger verifica se il file di simboli è presente in tale percorso.  
   
2. Nella stessa cartella della DLL o *.exe* file.
   
3. Tutti i percorsi specificati nelle opzioni del debugger per i file di simboli. Per aggiungere e abilitare i percorsi dei simboli, vedere [configurare i percorsi dei simboli e le opzioni di caricamento](#BKMK_Specify_symbol_locations_and_loading_behavior). 
   
   - Qualsiasi cartella della cache di simboli locale.  
  
   - Rete specificata, internet, o i server di simboli locale e posizioni, ad esempio server dei simboli Microsoft se selezionato. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può scaricare i file di simboli di debug dai server di simboli che implementano il `symsrv` protocollo. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) e il [strumenti di debug per Windows](/windows-hardware/drivers/debugger/index) sono due componenti che è possono utilizzare server dei simboli.
      
     È possibile utilizzare server dei simboli includono:  
      
     **Server di simboli Microsoft pubblici**: per eseguire il debug di un arresto anomalo del sistema che si verifica durante una chiamata a una DLL di sistema o a una libreria di terze parti, è spesso necessario sistema *PDB* file. System *PDB* contengono i simboli per le DLL di Windows, *.exe* file e i driver di dispositivo. È possibile ottenere i simboli per i sistemi operativi Windows, MDAC, IIS, ISA e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dai server dei simboli Microsoft pubblici. 
      
     **Server in una rete interna o nel computer locale di simboli**: team o dalla società può creare server di simboli per i propri prodotti e come cache dei simboli provenienti da origini esterne. Nel computer potrebbe essere presente un server di simboli. 
      
     **Server dei simboli di terze parti**: provider di terze parti di librerie e applicazioni di Windows può fornire l'accesso al server di simboli su internet. 
    
     > [!WARNING]
     > Se si usa un server di simboli diverso dal server di simboli Microsoft pubblici, assicurarsi che il server di simboli e il relativo percorso siano attendibili. Poiché i file di simboli possono contenere codice eseguibile arbitrario, può essere esposto a rischi di sicurezza.  

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Configurare le opzioni di caricamento e percorsi dei simboli

Nel **degli strumenti** > **opzioni** > **debug** > **simboli** pagina, è possibile:

- Specificare e selezionare i percorsi di ricerca e i server di simboli per Microsoft, Windows o i componenti di terze parti.
- Specificare i moduli o non desidera il debugger carichi automaticamente simboli.
- Modificare queste impostazioni mentre si esegue attivamente il debug. Visualizzare [gestire i simboli durante il debug](#manage-symbols-while-debugging). 
  
**Per specificare percorsi dei simboli e opzioni di caricamento:**

1. In Visual Studio, aprire **degli strumenti** > **opzioni** > **debug** > **simboli** (o **Debug** > **opzioni** > **simboli**).  
   
   ![Strumenti di &#45; opzioni &#45; debug &#45; pagina simboli](media/dbg-options-symbols.png "strumenti &#45; opzioni &#45; debug &#45; pagina simboli")  
   
2. Sotto **percorsi di file (con estensione pdb) di simboli**,
   - Usare la **server dei simboli Microsoft**, selezionare la casella di controllo.  
   
   - Per aggiungere una nuova posizione di server di simboli,
     1. Selezionare il **+** simbolo nella barra degli strumenti. 
     1. Digitare il percorso URL o la cartella del server di simboli o posizione del simbolo nel campo di testo. La funzione di completamento delle istruzioni facilita l'individuazione del formato corretto.
     
     >[!NOTE]
     >Viene eseguita la ricerca solo nella cartella specificata. È necessario aggiungere voci per eventuali sottocartelle che si desidera eseguire la ricerca.  
   
   - Per aggiungere una nuova posizione, il Server di simboli di Visual Studio Team Services 
     1. Selezionare il ![strumenti&#47; opzioni&#47; debug&#47;nuova icona di server dei simboli](media/dbg_tools_options_foldersicon.png "strumenti &#45; opzioni &#45; debug &#45; nuova icona di server dei simboli") icona sulla barra degli strumenti. 
     1. Nel **Connetti al Server di simboli di VSTS** finestra di dialogo, scegliere uno dei server dei simboli disponibili e selezionare **Connect**.  
   
   - Per modificare l'ordine di caricamento per i percorsi dei simboli, usare **Ctrl**+**backup** e **Ctrl**+**verso il basso**, o il **iscrizione** e **verso il basso** icone freccia. 
   - Per modificare un URL o percorso, fare doppio clic sulla voce, oppure selezionarlo e premere **F2**.  
   - Per rimuovere una voce, selezionarlo e quindi selezionare il **-** icona.
  
3. (Facoltativo) Per migliorare le prestazioni di caricamento dei simboli, sotto **memorizza nella Cache i simboli in questa directory**, un percorso di cartella locale che i server di simboli possono copiare i simboli per tipo.  
  
   > [!NOTE]
   > Cache dei simboli locale non viene inserito in una cartella protetta, ad esempio C:\Windows o una sottocartella. Usare invece una cartella di lettura e scrittura.  
  
   > [!NOTE]
   > Per i progetti C++, se si dispone di `_NT_SYMBOL_PATH` set di variabili di ambiente, eseguirà l'override del valore impostato in **memorizza nella Cache i simboli in questa directory**.
  
4. Specificare i moduli desiderati il debugger deve caricare dal **percorsi di file (con estensione pdb) di simboli** quando viene avviato.  
  
   -  Selezionare **caricare tutti i moduli, eccetto quelli esclusi** (predefinito) per caricare tutti i simboli per tutti i moduli nel percorso del file di simboli, ad eccezione di moduli escludere in modo specifico. Per escludere alcuni moduli, selezionare **specificare moduli esclusi**, selezionare la **+** icona, digitare i nomi dei moduli per escludere, quindi selezionare **OK**.  
  
   -  Per caricare solo i moduli specificati da percorsi dei file di simboli, selezionare **carico solo moduli specificati**. Selezionare **specificare moduli inclusi**, selezionare la **+** icona, digitare i nomi dei moduli da includere e quindi selezionare **OK**. I file di simboli per altri moduli non vengono caricati.  
  
5. Scegliere **OK**.

## <a name="other-symbol-options-for-debugging"></a>Altre opzioni di simboli di debug
  
È possibile selezionare le opzioni dei simboli aggiuntive nelle **degli strumenti** > **opzioni** > **debug** > **generale** (o **Debug** > **opzioni** > **generale**):  

- **Carica esportazioni DLL (solo nativo)**  
  
  Carica DLL esporta le tabelle per C/C++. Per informazioni dettagliate, vedere [tabelle di esportazione DLL](#use-dumpbin-exports). Informazioni di esportazione DLL durante la lettura comporta un sovraccarico, in modo che il caricamento delle tabelle di esportazione è stata disattivata per impostazione predefinita. È anche possibile usare `dumpbin /exports` in una riga di comando di compilazione di C/C++.  
  
- **Attiva debug a livello di indirizzo** e **Mostra disassembly se l'origine non disponibile**  
  
  Mostra sempre il disassembly quando i file di origine o di simboli non vengono trovati.  
  
  ![Le opzioni &#47; debug &#47; opzioni di disassembly generali](../debugger/media/dbg_options_general_disassembly_checkbox.png "opzioni &#47; debug &#47; opzioni di disassembly generale")  
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Abilitare il supporto del server di origine**  
  
  Usa il Server di origine per eseguire il debug di un'app quando non è disponibile codice sorgente nel computer locale, o la *PDB* file non corrisponde al codice sorgente. Server di origine riceve richieste di file e restituisce i file effettivi dal controllo del codice sorgente. Server di origine viene eseguito tramite una DLL denominata *SrcSrv* dell'app di leggere *PDB* file. Il *PDB* file contiene i puntatori al repository del codice sorgente, nonché i comandi utilizzati per recuperare il codice sorgente dal repository. 
  
  È possibile limitare i comandi che *SrcSrv* possono eseguire l'app *PDB* file eseguendo i comandi consentiti in un file denominato *SrcSrv*. Sul posto di *SrcSrv* file nella stessa cartella *SrcSrv* e *devenv.exe*.  
  
  >[!IMPORTANT]
  >I comandi arbitrari possono essere incorporati in un'app *PDB* del file, assicurarsi di inserire solo i comandi da eseguire in un *SrcSrv* file. Qualsiasi tentativo di eseguire un comando non incluso il *srcsvr* file causerà una finestra di dialogo di conferma da visualizzare. Per altre informazioni, vedere [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). 
  >
  >Poiché non viene eseguita alcuna convalida sui parametri dei comandi, prestare attenzione nell'utilizzare i comandi attendibili. Ad esempio, se è elencato *cmd.exe* nel *SrcSrv*, un utente malintenzionato potrebbe specificare parametri nel *cmd.exe* che potrebbe renderlo pericolosi.  
  
  Selezionare questo elemento e gli elementi figlio desiderati. **Consenti server origine per assembly parzialmente attendibili (solo gestito)** e **eseguire i comandi del server di origine non attendibili senza chiedere conferma sempre** possono aumentare i rischi di sicurezza.  
  
  ![Abilitare le opzioni relative ai server di origine](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  

## <a name="compiler-symbol-options"></a>Opzioni dei simboli del compilatore  

Quando si compila un progetto dall'IDE di Visual Studio con lo standard **Debug** configurazione della build, C++ e compilatori gestiti creano i file di simboli appropriati per il codice. È anche possibile impostare le opzioni del compilatore nel codice. 

### <a name="cc-options"></a>Opzioni C/C++ 

- *VC\<x > PDB* e  *\<progetto > PDB* file
  
  Oggetto *PDB* del file per C/C++ viene creato quando si compila con [/ZI o /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). Nella [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], il [/Fd](/cpp/build/reference/fd-program-database-file-name) opzione nomi il *PDB* il compilatore crea file. Quando si crea un progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizza l'IDE, le **/Fd** opzione è impostata per creare una *PDB* file denominato  *\<progetto > PDB*.  
  
  Se si compila l'applicazione C/C++ usando un makefile e specifica **/ZI** oppure **/Zi** senza usare **/Fd**, il compilatore crea due *PDB*i file:  
  
  - *VC\<x > PDB*, dove  *\<x >* rappresenta la versione di Visual C++, ad esempio *VC11.pdb* 
    
    Il *VC\<x > PDB* archivia tutte le informazioni di debug per i file oggetto singoli file e si trova nella stessa directory del progetto makefile. Ogni volta che viene creato un file oggetto, il compilatore C/C++ unisce le informazioni di debug in *VC\<x > PDB*. Pertanto, anche se ogni file di origine include file di intestazione comuni, ad esempio  *\<Windows. h >*, i typedef di tali intestazioni vengono archiviati una sola volta, anziché in ogni file oggetto. Le informazioni inserite includono informazioni sul tipo, ma non includano informazioni sui simboli, quali le definizioni di funzione.  
  
  - *\<progetto > con estensione pdb* 
    
    Il  *\<progetto > PDB* file vengono archiviate tutte le informazioni di debug per il progetto *.exe* file e si trova nel *\debug* sottodirectory. Il  *\<progetto > PDB* file contiene le informazioni di debug completa, inclusi i prototipi di funzione non solo le informazioni sui tipi disponibili *VC\<x > PDB*. 
  
  Entrambi i *VC\<x > PDB* e  *\<progetto > PDB* file supportano gli aggiornamenti incrementali. Il linker incorpora inoltre il percorso per il *PDB* i file nella *.exe* o *. dll* file creato.  
  
- <a name="use-dumpbin-exports"></a>Tabelle di esportazione DLL
  
  Usare `dumpbin /exports` per visualizzare i simboli disponibili nella tabella di esportazione di una DLL. Informazioni sui simboli delle tabelle di esportazione DLL possono essere utile per l'utilizzo di messaggi di Windows, routine Windows (WindowProc), COM oggetti, marshalling o qualsiasi DLL non si dispone di simboli per. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. 
  
  Leggendo la `dumpbin /exports` di output, è possibile visualizzare i nomi di funzione exact, inclusi i caratteri non alfanumerici. Visualizzare i nomi delle funzioni esatta è utile per impostare un punto di interruzione in una funzione, perché i nomi delle funzioni possono essere troncate in altre posizioni nel debugger. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
### <a name="net-framework-options"></a>Opzioni di .NET Framework 
  
Compilazione con **/debug** per creare un *PDB* file. È possibile compilare applicazioni con **/debug:full** o **/debug:pdbonly**. Se si usa l'opzione di compilazione **/debug:full** , verrà generato codice di cui è possibile effettuare il debug. Compilazione con **/debug: pdbonly** genera *PDB* i file, ma non genera il `DebuggableAttribute` che indica al compilatore JIT che sono disponibili informazioni di debug. Uso **/debug: pdbonly** se si desidera generare *PDB* file per una versione di compilazione che non si desidera sottoporre a debug. Per altre informazioni, vedere [/debug (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) oppure [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).  
  
### <a name="web-applications"></a>Applicazioni Web  
  
Impostare il *Web. config* file dell'applicazione ASP.NET in modalità debug. Tramite la modalità di debug, ASP.NET genera simboli per i file generati dinamicamente e il debugger si collega all'applicazione ASP.NET. Visual Studio configura automaticamente questa impostazione quando si avvia il debug, se è stato creato il progetto dal modello dei progetti web.  

##  <a name="manage-symbols-while-debugging"></a>Gestire i simboli durante il debug 

È possibile usare la **moduli**, **Stack di chiamate**, **variabili locali**, **Auto**, o qualsiasi **Watch** finestra da caricare i simboli o modifica le opzioni dei simboli durante il debug. Per altre informazioni, vedere [acquisire maggiore familiarità con la modalità con cui il debugger si connette all'app](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="use-the-modules-window"></a>Utilizzare la finestra moduli

Durante il debug, il **moduli** finestra Mostra i moduli di codice il debugger è trattare come codice utente, o My Code e i simboli di caricamento dello stato. È anche possibile monitorare lo stato di caricamento dei simboli, caricare i simboli e modificare le opzioni dei simboli nel **moduli** finestra.

**Per monitorare o modificare percorsi di simboli o opzioni durante il debug:**

1. Per aprire la **moduli** finestra durante il debug, selezionare **Debug** > **Windows** > **moduli**. 
1. Nel **moduli** finestra, fare doppio clic sul **stato simboli** oppure **File di simboli** intestazioni o qualsiasi modulo. 
1. Nel menu di scelta rapida, selezionare una delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Carica simboli**|Viene visualizzata per i moduli con i simboli ignorati, non è stati trovati o non è stati caricati. Tenta di caricare i simboli dai percorsi specificati nella **le opzioni** > **debug** > **simboli** pagina. Se il file di simboli non trovato o non caricato, viene avviata **Esplora File** quindi è possibile specificare un nuovo percorso da cercare.|  
|**Informazioni sul caricamento simboli**|Mostra la posizione di un file di simboli caricato o i percorsi cercati se il debugger non è possibile trovare il file.|  
|**Impostazioni simboli**|Apre la **le opzioni** > **debug** > **simboli** pagina, in cui è possibile modificare e aggiungere i percorsi dei simboli.|  
|**Caricare sempre automaticamente**|Aggiunge il file di simboli selezionati all'elenco di file che vengono caricati automaticamente dal debugger.|  

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Usare le pagine Nessuna simboli Loaded/No origine caricata

Esistono diversi modi per il debugger inserire un'interruzione nel codice che non esistono file di simboli o di origine disponibili:  

-  L'istruzione nel codice.  
-  Inserire un'interruzione nel codice da un punto di interruzione o eccezione.  
-  Passare a un altro thread.  
-  Cambiare lo stack frame facendo doppio clic su un frame nel **Stack di chiamate** finestra.  
   
In questo caso, il debugger visualizza i **Nessun simbolo caricato** oppure **Nessuna origine caricata** pagine che consentono di individuare e caricare l'origine o dei simboli necessari.  
  
 ![Pagina Nessun simbolo caricato](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
**Per usare la pagina del documento Nessun simbolo caricato per trovare e caricare i simboli mancanti:**  
  
-   Per modificare il percorso di ricerca, selezionare un percorso non selezionato o selezionare **nuovo percorso** oppure **nuovo percorso VSTS** e immettere o selezionare un nuovo percorso. Selezionare **caricare** per cercare nuovamente i percorsi e caricare il file di simboli se viene trovato.  
-   Per eseguire l'override di tutte le opzioni dei simboli e ripetere i percorsi di ricerca, selezionare **cercare e trovare \<nome eseguibile >**. Il file di simboli viene caricato se viene trovato, o **Esplora File** apre in modo che è possibile selezionare manualmente il file di simboli.  
-   Per aprire la **le opzioni** > **debug** > **simboli** selezionare **Cambia impostazioni simboli**.  
-   Per visualizzare il disassembly in una nuova finestra una volta, selezionare **visualizzare il disassembly**, o selezionare **finestra di dialogo Opzioni** per impostare l'opzione per visualizzare sempre il disassembly quando i file di origine o di simboli non vengono trovati. 
-   Per visualizzare i percorsi di ricerca e il risultato, espandere **informazioni sul caricamento simboli**. 

Se il debugger rileva il *PDB* file dopo l'esecuzione di una delle opzioni e può recuperare file di origine utilizzando le informazioni contenute nel *PDB* file, Visualizza l'origine. In caso contrario, viene visualizzato un **Nessuna origine caricata** pagina che descrive il problema, con collegamenti alle azioni che potrebbero risolvere il problema.

**Per aggiungere i percorsi di ricerca di file di origine a una soluzione:**
  
È possibile specificare i percorsi in cui il debugger cerca i file di origine ed escludere i file specifici dalla ricerca.

1. Selezionare la soluzione in **Esplora soluzioni**, quindi selezionare il **delle proprietà** icona, premere **Alt**+**invio**, o Fare doppio clic e selezionare **proprietà**.
   
1. Selezionare **eseguire il Debug di file di origine**.
   
1. Sotto **directory contenenti codice sorgente**digitare o selezionare i percorsi del codice sorgente per la ricerca. Usare la **nuova riga** icona per aggiungere più posizioni, il **backup** e **verso il basso** icone freccia per riordinarli, o il **X** icona per eliminarli.
   
   >[!NOTE]
   >Il debugger cerca solo nella directory specificata. È necessario aggiungere voci per qualsiasi sottodirectory da cercare.
   
1. Sotto **non cercare questi file di origine**, digitare i nomi dei file di origine da escludere dalla ricerca. 
   
1. Selezionare **OK** oppure **applicare**.


## <a name="see-also"></a>Vedere anche  
[Comprendere i file di simboli e le impostazioni dei simboli di Visual Studio](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)

[.NET caricamento remoto dei simboli modifiche in Visual Studio 2012 e 2013](https://blogs.msdn.microsoft.com/devops/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
