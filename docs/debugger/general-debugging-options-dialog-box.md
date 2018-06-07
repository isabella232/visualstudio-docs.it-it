---
title: Generale, debug, finestra di dialogo Opzioni | Documenti Microsoft
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
ms.openlocfilehash: 5b7af8c68764b3a9ed85bf6a52a3a6c4a0568203
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572050"
---
# <a name="general-debugging-options-dialog-box"></a>Generale, Debug, finestra di dialogo Opzioni
Il **strumenti > Opzioni > Debug > Generale** pagina consente di configurare le opzioni descritte in questo articolo.

Se è necessario ripristinare le impostazioni predefinite, è possibile eseguire tale usando **Tools** > **Importa / Esporta impostazioni** > **Reimposta tutte le impostazioni**. Se si desidera reimpostare un subset di impostazioni, salvare le impostazioni nel **importazione / esportazione guidata delle impostazioni** prima di apportare le modifiche che si desidera testare, quindi importare le impostazioni salvate in un secondo momento.
  
**Chiedi prima di eliminare tutti i punti di interruzione** richiede una conferma prima di completare la **eliminare tutti i punti di interruzione** comando.  
  
**Quando si interrompe un processo, interrompi tutti i processi** interrompe simultaneamente tutti i processi a cui è connesso il debugger, quando si verifica un'interruzione.  
  
**Interrompi quando le eccezioni superano il dominio applicazione o i limiti gestiti/nativi** durante il debug gestito o in modalità mista, common language runtime può intercettare le eccezioni che superano i limiti del dominio applicazione o i limiti gestiti/nativi quando seguenti le condizioni sono vere:  
  
1\) quando il codice nativo chiama codice gestito mediante interoperabilità COM e il codice gestito genera un'eccezione. Vedere [Introduzione all'interoperabilità COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Vedere [programmazione con i domini applicazione](/dotnet/articles/framework/app-domains/index).  

3\) quando viene richiamata la funzione tramite reflection e la funzione genera un'eccezione. Vedere [Reflection](/dotnet/framework/reflection-and-codedom/reflection).  
  
Nella condizione 2 e 3, l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` anziché da common language runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.  
  
**Abilitare il debug a livello di indirizzo** Abilita le funzionalità avanzate per il debug a livello di indirizzo (la **Disassembly** finestra, il **registra** finestra e punti di interruzione).  
  
- **Mostra disassembly se l'origine non è disponibile** verrà visualizzato il **Disassembly** finestra quando si tenta di eseguire il debug di codice per l'origine è disponibile.  
  
**Abilita i filtri dei punti di interruzione** consente di applicare filtri ai punti di interruzione in modo che abbiano effetto su solo determinati processi, thread o computer.  
 
**Utilizzare il nuovo Helper eccezioni** consente il supporto di eccezioni (Visual Studio 2017) che sostituisce le informazioni sulle eccezioni.
  
> [!NOTE]
> Per codice gestito, questa opzione è stato precedentemente chiamata **Abilita informazioni sulle eccezioni** . 
  
**Abilita Just My Code** il debugger consente di visualizzare e i passaggi nel codice utente ("My Code"), ignorando il codice di sistema e altro codice ottimizzato o privo di simboli di debug.

- **Avvisa se all'avvio (solo gestito) Nessun codice utente** all'avvio del debug con Just My Code attivata, questa opzione Avvisa l'utente se non vi è nessun codice utente ("My Code"). 

**Abilitare .NET Framework esecuzione di istruzioni origine** consente al debugger di eseguire nell'origine di .NET Framework. L'abilitazione di questa opzione disabilita automaticamente Just My Code. I simboli .NET Framework saranno scaricati in un percorso della cache. È possibile modificare il percorso della cache nel **opzioni** nella finestra di dialogo **debug** categoria **simboli** pagina.  
  
**Esegui istruzione/routine di proprietà e operatori (solo gestito)** impedisce al debugger di eseguire istruzioni di proprietà e operatori nel codice gestito.  
  
**Abilita valutazione delle proprietà e altre chiamate di funzioni implicite** attiva la valutazione automatica delle proprietà e funzioni implicite chiamate nelle finestre delle variabili e i **controllo immediato** finestra di dialogo.  
  
- **Chiama la funzione di conversione di stringhe su oggetti nelle finestre delle variabili (c# e JavaScript solo)** esegue una chiamata di conversione di stringhe implicita durante la valutazione di oggetti nelle finestre delle variabili. Il risultato viene visualizzato come una stringa anziché il nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sostituita dall'attributo DebuggerDisplay (vedere [utilizzando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Abilita il supporto di server di origine** indica al debugger di Visual Studio per ottenere i file di origine dai server di origine che implementano il SrcSrv (`srcsrv.dll`) protocollo. Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per ulteriori informazioni sull'installazione di SrcSrv, vedere il [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) documentazione. Inoltre, vedere [specificare simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Poiché la lettura dei file PDB può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.  
  
- **Visualizza origine server i messaggi diagnostici nella finestra di Output** quando è abilitato il supporto del server di origine, questa impostazione attiva la visualizzazione di diagnostica.  
  
- **Consenti server origine per assembly parzialmente attendibili (solo gestito)** quando è abilitato il supporto del server di origine, questa impostazione sostituisce il comportamento predefinito di non recupera le origini per gli assembly parzialmente attendibili.  

**Abilitare il supporto di origine collegamento** indica al debugger di Visual Studio per scaricare i file di origine per i file con estensione PDB che contengono informazioni sui collegamenti di origine. Per ulteriori informazioni sul collegamento di origine, vedere il [specifica di collegamento di origine](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Evidenzia intera riga per i punti di interruzione e l'istruzione corrente (solo C++)** quando il debugger evidenzia un punto di interruzione e l'istruzione corrente, estende l'evidenziazione all'intera riga.  
  
**Richiede i file di origine da corrispondere esattamente alla versione originale** indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile sottoposto a debug. Se la versione non corrisponde, chiesto di trovare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug. 
  
**Reindirizza tutto il testo finestra Output nella finestra controllo immediata** invia tutti i messaggi del debugger che normalmente verrebbero visualizzati nella **Output** finestra per il **immediato** finestra invece.  
  
**Mostra struttura non elaborata degli oggetti nelle finestre delle variabili** Disattiva tutte le personalizzazioni di visualizzazione struttura di oggetti. Per ulteriori informazioni sulla personalizzazione delle visualizzazioni, vedere [creare viste personalizzate di oggetti .managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Disattiva l'ottimizzazione JIT al caricamento del modulo (solo gestito)** disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato mentre il debugger è collegato. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code"). Per ulteriori informazioni, vedere [debug e ottimizzazione JIT](../debugger/jit-optimization-and-debugging.md).

**Abilitare il debug di JavaScript per ASP.NET (Chrome e Internet Explorer)** consente al debugger di script per le applicazioni ASP.NET. Al primo utilizzo in Chrome, è necessario accedere al primo utilizzo per abilitare le estensioni di colore che è stato installato il browser. Disabilitare questa opzione per ripristinare il comportamento legacy.    

**Carica esportazioni dll** carica tabelle di esportazione dll. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.  
  
Per visualizzare i simboli sono disponibili nella tabella di esportazione di una dll, utilizzare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports` , è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Dal basso in alto diagramma degli stack in parallelo di presentazione** controlla la direzione in cui vengono visualizzati gli stack nella **stack in parallelo** finestra.
  
**Ignora eccezioni di accesso di memoria GPU se i dati scritti non hanno modificato il valore** ignora le race condition rilevate durante il debug se i dati non sono stati modificati. Per ulteriori informazioni, vedere [debug del codice GPU](../debugger/debugging-gpu-code.md).  
  
**Utilizzare la modalità di compatibilità gestita** sostituisce il motore debug predefinito con una versione legacy per abilitare gli scenari seguenti:  
  
- Si utilizza un linguaggio .NET Framework diverso da C#, VB o F# che fornisce il proprio analizzatore di espressioni (questo include C++/CLI).  
  
- Si vuole abilitare Modifica e continuazione per i progetti C++ durante il debug in modalità mista.  
  
> [!NOTE]
> Modalità scelta di compatibilità gestita vengono disabilitate alcune funzionalità implementate solo nel motore di debug predefinito. 

**Usa gli analizzatori di espressioni c# e VB legacy** il debugger userà gli analizzatori di espressioni di Visual Studio 2013 C# /VB anziché gli analizzatori di espressioni basate su Visual Studio 2015 Roslyn.    
  
**Avvisa quando si usano visualizzatori di debugger personalizzati in processi potenzialmente non sicuri (solo gestito)** Visual Studio genera avvisi quando si utilizza un visualizzatore di debugger personalizzato che esegue codice nel processo oggetto del debug perché potrebbe essere in esecuzione unsafe codice.  
  
**Abilita l'allocatore di heap di debug Windows (solo nativo)** consente l'heap di debug di windows migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.  
  
**Abilita strumenti di debug dell'interfaccia utente per XAML** l'albero elementi visivi attivi e le finestre Esplora proprietà attive vengono visualizzate quando si avvia il debug (F5) un tipo di progetto supportato. Per ulteriori informazioni, vedere [proprietà controllare XAML durante il debug](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Anteprima degli elementi selezionati in albero elementi visivi attivi** XAML il cui contesto viene selezionato viene anche selezionato nel **albero elementi visivi attivi** finestra.  
  
- **Mostra strumenti di runtime nell'applicazione** Mostra il **albero elementi visivi attivi** comandi in una barra degli strumenti nella finestra principale dell'applicazione XAML in cui viene eseguito il debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2. 

- **Abilitare XAML modifica e continuazione** consente di utilizzare Modifica e continuazione di funzionalità per il codice XAML. 
  
**Abilita strumenti di diagnostica durante il debug** il **strumenti di diagnostica** verrà visualizzata la finestra durante il debug.
  
**Mostra il perftip relativo al tempo trascorso durante il debug** finestra del codice visualizza il tempo trascorso di una chiamata al metodo specificato quando si esegue il debug.  
  
**Abilitare Modifica e continuazione** è possibile usare la modifica e continuazione funzionalità durante il debug.  
  
- **Abilita modifica e continuazione nativo** è possibile usare la modifica e continuazione funzionalità durante il debug del codice C++ nativo. Per ulteriori informazioni, vedere [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Applicare le modifiche durante la continuazione (solo nativo)** Visual Studio viene compilato automaticamente e applica le modifiche di codice in sospeso apportate quando continuare il processo da uno stato di interruzione. Se non è selezionata, è possibile scegliere di applicare le modifiche utilizzando l'elemento "Applica modifiche del codice" nel menu Debug.  
  
- **Avvisa in codice non aggiornato (solo nativo)** ricevere avvisi relativi al codice non aggiornato.    

**Mostra esecuzione fare clic sul pulsante nell'editor durante il debug** quando questa opzione è selezionata, il [eseguire fare clic su](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) pulsante verrà visualizzato durante il debug.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opzioni supportate nelle versioni precedenti di Visual Studio

Se si utilizza una versione precedente di Visual Studio, è possibile che alcune opzioni aggiuntive potrebbero essere presenti.

**Abilita informazioni sulle eccezioni** per codice gestito, abilitare le informazioni sulle eccezioni. In Visual Studio 2017, l'Helper eccezioni sostituito informazioni sulle eccezioni.

**Rimuovi stack di chiamate su eccezioni non gestite** fa sì che il **Stack di chiamate** finestra rollback lo stack di chiamate al punto precedente l'eccezione non gestita. 

**Avvisa se non vi sono simboli all'avvio (solo nativo)** Visualizza una finestra di dialogo di avviso quando si tenta di eseguire il debug di un programma per il quale il debugger non ha alcuna informazione sui simboli. 

**Avvisa se il debug degli script è disabilitato all'avvio** Visualizza una finestra di dialogo di avviso quando il debugger viene avviato con il debug degli script disabilitato.

**Utilizzare la modalità di compatibilità nativa** quando questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.  
  
Usare questa opzione quando si esegue il debug di codice C++ .NET perché il nuovo motore di debug non supporta la valutazione delle espressioni C++ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non ha molti dei visualizzatori per i tipi incorporati come `std::string` nei progetti di Visual Studio 2015.   Utilizzare i progetti di Visual Studio 2013 per l'esperienza di debug ottimale in questi casi.
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
