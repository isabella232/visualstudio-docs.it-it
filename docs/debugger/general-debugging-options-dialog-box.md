---
title: Generale, debug, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e46301c84b1a9b27eed8cb6667b312ff73af2960
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280637"
---
# <a name="general-debugging-options-dialog-box"></a>Generale, Debug, finestra di dialogo Opzioni
Il **strumenti > Opzioni > Debug > Generale** pagina consente di impostare le opzioni descritte in questo articolo.

Se si vuole ripristinare le impostazioni predefinite, è possibile farlo tramite **degli strumenti** > **Importa / Esporta impostazioni** > **Reimposta tutte le impostazioni**. Se vuoi solo ripristinare un subset di impostazioni, salvare le impostazioni nel **importazione / esportazione guidata delle impostazioni** prima di apportare le modifiche che si vuole testare, quindi importare le impostazioni salvate in un secondo momento.
  
**Chiedi prima di eliminare tutti i punti di interruzione** richiede la conferma prima di completare le **eliminare tutti i punti di interruzione** comando.  
  
**Quando si interrompe un processo, interrompi tutti i processi** interrompe simultaneamente tutti i processi a cui è collegato il debugger, quando si verifica un'interruzione.  
  
**Interrompi quando le eccezioni superano il dominio dell'applicazione o i limiti gestiti/nativi** durante il debug gestito o in modalità mista, common language runtime può intercettare le eccezioni che superano i limiti del dominio dell'applicazione o i limiti gestiti/nativi quando seguenti le condizioni sono vere:  
  
1\) quando codice nativo chiama il codice gestito mediante interoperabilità COM e il codice gestito genera un'eccezione. Visualizzare [Introduzione all'interoperabilità COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Visualizzare [programmazione con domini applicazione](/dotnet/articles/framework/app-domains/index).  

3\) quando viene richiamata la funzione tramite reflection e la funzione genera un'eccezione. Visualizzare [Reflection](/dotnet/framework/reflection-and-codedom/reflection).  
  
Nella condizione 2 e 3, l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` invece di common language runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.  
  
**Abilitare il debug a livello di indirizzo** Abilita le funzionalità avanzate per il debug a livello di indirizzo (la **Disassembly** finestra, il **registra** finestra e punti di interruzione).  
  
- **Mostra disassembly se l'origine non è disponibile** Mostra automaticamente il **Disassembly** finestra quando si prova a eseguire il debug di codice per cui l'origine non è disponibile.  
  
**Abilita i filtri dei punti di interruzione** ti permette di applicare filtri ai punti di interruzione in modo che influiranno solo determinati processi, thread o computer.  
 
**Usare il nuovo Helper eccezioni** consente il supporto di eccezioni (Visual Studio 2017) che sostituisce le informazioni sulle eccezioni.
  
> [!NOTE]
> Per codice gestito, questa opzione è stata chiamata precedentemente **Abilita informazioni sulle eccezioni** . 
  
**Abilitare Just My Code** il debugger consente di visualizzare e i passaggi nel codice utente ("My Code"), ignorando il codice di sistema e altro codice ottimizzato o che non dispone i simboli di debug.

- **Avvisa se all'avvio (solo gestito) Nessun codice utente** all'avvio del debug con Just My Code abilitato, questa opzione Avvisa l'utente se non è presente codice utente ("My Code"). 

**Abilitare .NET Framework esecuzione di istruzioni origine** consente al debugger di eseguire l'istruzione di codice sorgente di .NET Framework. L'abilitazione di questa opzione disabilita automaticamente Just My Code. I simboli .NET Framework saranno scaricati in un percorso della cache. È possibile modificare il percorso della cache nel **le opzioni** della finestra di dialogo **debug** categoria **simboli** pagina.  
  
**Esegui istruzione/routine di proprietà e operatori (solo gestito)** impedisce al debugger di eseguire istruzioni di proprietà e operatori nel codice gestito.  
  
**Abilita valutazione delle proprietà e altre chiamate di funzioni implicite** attiva la valutazione automatica delle proprietà e funzioni implicite chiamate nelle finestre delle variabili e le **controllo immediato** nella finestra di dialogo.  
  
- **Chiama la funzione di conversione delle stringhe su oggetti nelle finestre delle variabili (c# e JavaScript solo)** esegue una chiamata di conversione di stringhe implicita durante la valutazione di oggetti nelle finestre delle variabili. Il risultato viene visualizzato come stringa anziché il nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sottoposto a override mediante l'attributo DebuggerDisplay (vedere [usando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Abilitare il supporto del server di origine** indica al debugger di Visual Studio per ottenere i file di origine dai server di origine che implementano il SrcSrv (`srcsrv.dll`) protocollo. Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per altre informazioni sull'installazione di SrcSrv, vedere la [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) documentazione. Inoltre, vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Poiché leggendo *PDB* file possono eseguire codice arbitrario nei file, assicurarsi che si ritiene attendibile il server.  
  
- **Visualizza origine server i messaggi diagnostici nella finestra di Output** quando è abilitato il supporto del server di origine, questa impostazione attiva la visualizzazione di diagnostica.  
  
- **Consenti server origine per assembly parzialmente attendibili (solo gestito)** quando è abilitato il supporto del server di origine, questa impostazione sostituisce il comportamento predefinito non recupera le origini per assembly parzialmente attendibili.  

**Abilitare il collegamento all'origine supporto** indica al debugger di Visual Studio per scaricare i file di origine per i file con estensione PDB che contengono informazioni sui collegamenti di origine. Per altre informazioni sul collegamento all'origine, vedere la [specifica l'origine collegamento](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Evidenzia intera riga per i punti di interruzione e l'istruzione corrente (solo C++)** quando il debugger evidenzia un punto di interruzione e l'istruzione corrente, evidenzia l'intera riga.  
  
**Richiedere i file di origine a una corrispondenza esatta tra la versione originale** indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile di cui si esegue il debug. Se la versione non corrisponde, chiesto di trovare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug. 
  
**Reindirizza tutto il testo di finestra di Output nella finestra controllo immediata** invia tutti i messaggi del debugger che normalmente verrebbero visualizzati nella **Output** finestra per il **immediato** finestra invece.  
  
**Mostra struttura non elaborata degli oggetti nelle finestre delle variabili** consente di disattivare tutte le personalizzazioni della visualizzazione struttura oggetto. Per altre informazioni sulla personalizzazione delle visualizzazioni, vedere [creare viste personalizzate di oggetti. Managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Disattiva l'ottimizzazione JIT al caricamento del modulo (solo gestito)** disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato al momento della connessione al debugger. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code"). Per altre informazioni, vedere [debug e ottimizzazione JIT](../debugger/jit-optimization-and-debugging.md).

**Abilita il debug di JavaScript per ASP.NET (Chrome e inserimento/espulsione)** consente al debugger di script per le app ASP.NET. Al primo utilizzo in Chrome, potrebbe essere necessario accedere al primo utilizzo per abilitare le estensioni Chrome che è stato installato il browser. Disabilitare questa opzione per ripristinare il comportamento legacy.    

**Carica esportazioni dll** carica le tabelle di esportazione dll. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.  
  
Per visualizzare i simboli sono disponibili nella tabella di esportazione di una dll, usare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports` , è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Dal basso in alto diagramma degli stack in parallelo di Show** controlla la direzione in cui vengono visualizzati gli stack nel **stack in parallelo** finestra.
  
**Ignora eccezioni di accesso a memoria GPU se i dati scritti non hanno modificato il valore** ignora le race condition rilevate durante il debug se i dati non sono state modificate. Per altre informazioni, vedere [debug del codice GPU](../debugger/debugging-gpu-code.md).  
  
**Usare modalità di compatibilità gestita** sostituisce il motore con una versione legacy per consentire questi scenari di debug predefinito:  
  
- Si utilizza un linguaggio .NET Framework diverso da C#, VB o F# che fornisce il proprio analizzatore di espressioni (questo include C++/CLI).  
  
- Si vuole abilitare Modifica e continuazione per i progetti C++ durante il debug in modalità mista.  
  
> [!NOTE]
> Modalità la scelta di compatibilità gestita vengono disabilitate alcune funzionalità implementate solo nel motore di debug predefinito. 

**Usa gli analizzatori di espressioni c# e VB legacy** il debugger userà gli analizzatori di espressioni di Visual Studio 2013 C# /VB anziché gli analizzatori di espressioni basate su Visual Studio 2015 Roslyn.    
  
**Avvisa quando si usano visualizzatori di debugger personalizzati processi potenzialmente non sicuri (solo gestito)** Visual Studio genera avvisi quando si usa un visualizzatore di debugger personalizzata che esegue codice nel processo oggetto del debug perché potrebbe essere in esecuzione non sicuro codice.  
  
**Abilita l'allocatore di heap di debug Windows (solo nativo)** consente l'heap di debug windows migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.  
  
**Abilita strumenti di debug dell'interfaccia utente per XAML** verranno visualizzato l'albero elementi visivi attivi e le finestre Esplora proprietà attive all'avvio del debug (F5) un tipo di progetto supportati. Per altre informazioni, vedere [delle proprietà di ispezionare XAML durante il debug](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Anteprima degli elementi selezionati in albero elementi visivi attivi** elemento XAML il cui contesto viene selezionato viene selezionata anche nella **albero elementi visivi attivi** finestra.  
  
- **Mostra strumenti di runtime nell'applicazione** Mostra il **albero elementi visivi attivi** comandi in una barra degli strumenti nella finestra principale dell'applicazione XAML in fase di debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2. 

- **Abilitare XAML modifica e continuazione** consente di usare modifica e continuazione funzionalità per il codice XAML. 
  
**Abilita strumenti di diagnostica durante il debug** il **strumenti di diagnostica** verrà visualizzata la finestra durante il debug.
  
**Mostra il perftip relativo al tempo trascorso durante il debug** finestra del codice visualizza il tempo trascorso di una chiamata al metodo specificato quando si esegue il debug.  
  
**Abilita modifica e continuazione** è possibile usare modifica e la funzionalità di continuazione durante il debug.  
  
- **Abilita modifica e continuazione nativo** è possibile usare modifica e la funzionalità di continuazione durante il debug del codice C++ nativo. Per altre informazioni, vedere [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Applicare le modifiche durante la continuazione (solo nativo)** Visual Studio viene compilato automaticamente e applica modifiche al codice in sospeso apportate quando continuare il processo da uno stato di interruzione. Se non è selezionata, è possibile scegliere di applicare le modifiche usando l'elemento "Applica modifiche del codice" nel menu Debug.  
  
- **Avvisa in codice non aggiornato (solo nativo)** ricevere avvisi relativi al codice non aggiornato.    

**Mostra esecuzione fare clic sul pulsante nell'editor durante il debug** quando questa opzione è selezionata, il [Esegui fino al clic](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) pulsante verrà visualizzato durante il debug.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opzioni supportate nelle versioni precedenti di Visual Studio

Se si usa una versione precedente di Visual Studio, alcune opzioni aggiuntive potrebbero essere presenti.

**Abilita informazioni sulle eccezioni** per codice gestito, abilitare le informazioni sulle eccezioni. In Visual Studio 2017, l'Helper eccezioni sostituito informazioni sulle eccezioni.

**Rimuovi stack di chiamate su eccezioni non gestite** fa sì che il **Stack di chiamate** finestra eseguire il rollback dello stack di chiamate al punto prima che si è verificata un'eccezione non gestita. 

**Avvisa se non vi sono simboli all'avvio (solo nativo)** Visualizza una finestra di dialogo di avviso quando si prova a eseguire il debug di un programma per il quale il debugger non dispone di alcuna informazione sui simboli. 

**Avvisa se il debug degli script è disabilitato all'avvio** Visualizza una finestra di dialogo di avviso quando il debugger viene avviato con il debug degli script disabilitato.

**Utilizzare la modalità di compatibilità nativa** quando questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.  
  
Usare questa opzione quando si esegue il debug di codice C++ .NET perché il nuovo motore di debug non supporta la valutazione delle espressioni C++ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non contiene molti dei visualizzatori per i tipi incorporati, ad esempio `std::string` nei progetti di Visual Studio 2015.   Usare i progetti di Visual Studio 2013 per l'esperienza di debug ottima in questi casi.
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
