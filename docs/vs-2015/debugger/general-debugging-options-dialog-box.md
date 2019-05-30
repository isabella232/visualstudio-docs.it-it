---
title: Generale, debug, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47db517bfb75d81785e910d1dd166ac83ddb2fcb
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261662"
---
# <a name="general-debugging-options-dialog-box"></a>Generale, Debug, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il**Strumenti / opzioni / debug / generale** pagina consente di impostare le opzioni seguenti:  
  
 **Chiedi prima di eliminare tutti i punti di interruzione**  
 Richiede conferma prima dell'esecuzione del comando **Elimina tutti i punti di interruzione**.  
  
 **Quando si interrompe un processo, interrompi tutti i processi**  
 Interrompe simultaneamente tutti i processi a cui è connesso il debugger quando si verifica un'interruzione.  
  
 **Interrompi quando le eccezioni superano il dominio dell'applicazione o i limiti gestiti/nativi**  
 Durante il debug in modalità gestita o mista, Common Language Runtime è in grado di rilevare eccezioni che superano i limiti del dominio applicazione o i limiti gestiti/nativi quando sono vere le seguenti condizioni:  
  
 1\) quando codice nativo chiama il codice gestito mediante interoperabilità COM e il codice gestito genera un'eccezione. Visualizzare [Introduzione all'interoperabilità COM](https://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2\) quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Visualizzare [programmazione con domini applicazione](https://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) quando viene richiamata la funzione tramite reflection e la funzione genera un'eccezione. Visualizzare [Reflection](https://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 Nei casi 2) e 3) l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` anziché da Common Language Runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.  
  
 **Abilitare il debug a livello di indirizzo**  
 Abilita le funzionalità avanzate per il debug a livello di indirizzo (finestra **Disassembly**, finestra **Registri** e punti di interruzione).  
  
 **Mostra disassembly se l'origine non è disponibile**  
 Mostra automaticamente il **Disassembly** finestra quando si prova a eseguire il debug di codice per cui l'origine non è disponibile.  
  
 **Abilita i filtri dei punti di interruzione**  
 Consente di applicare filtri ai punti di interruzione in modo che abbiano effetto solo su determinati processi, thread o computer.  
  
 **Abilita informazioni sulle eccezioni**  
 Solo per il codice gestito. Le eccezioni gestite aprono la finestra di dialogo Informazioni sulle eccezioni.  Visualizzare [informazioni sulle eccezioni](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Rimuovi stack di chiamate su eccezioni non gestite**  
 La finestra **Stack di chiamate** esegue il rollback dello stack di chiamate al punto precedente l'eccezione non gestita.  
  
 **Abilitare Just My Code**  
 Il debugger visualizza ed esegue solo il codice utente ("My Code"), ignorando il codice di sistema e altro codice ottimizzato o privo di simboli di debug.  
  
 **Mostra tutti i membri per gli oggetti non utente nelle finestre delle variabili (solo Visual Basic)**  
 Attiva la visualizzazione dei membri non pubblici per gli oggetti presenti nel codice non utente (non "My Code").  
  
 **Avvisa se all'avvio nessun codice utente**  
 Quando il debug viene avviato con Just My Code attivato, questa opzione determina la visualizzazione di un avviso se non è presente codice utente ("My Code").  
  
 **Abilitare .NET Framework l'esecuzione di istruzioni di origine**  
 Consente al debugger di eseguire l'origine di .NET Framework. L'abilitazione di questa opzione disabilita automaticamente Just My Code. I simboli .NET Framework saranno scaricati in un percorso della cache. È possibile modificare il percorso della cache nel **le opzioni** della finestra di dialogo **debug** categoria **simboli** pagina.  
  
 **Esegui istruzione/routine di proprietà e operatori (solo gestiti)**  
 Impedisce al debugger di eseguire istruzioni di proprietà e operatori nel codice gestito.  
  
 **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**  
 Attiva la valutazione automatica di proprietà e altre chiamate di funzioni implicite nelle finestre delle variabili e nella finestra di dialogo **Controllo immediato**.  
  
 **Chiama la funzione di conversione delle stringhe su oggetti nelle finestre delle variabili (c# e solo JavaScript)**  
 Esegue una chiamata di conversione delle stringhe implicita durante la valutazione di oggetti nelle finestre delle variabili. Pertanto, il risultato viene visualizzato come stringa anziché come nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sottoposto a override mediante l'attributo DebuggerDisplay (vedere [usando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Abilita il supporto del server di origine**  
 Indica al debugger di Visual Studio di ottenere i file di origine da server di origine che implementano il protocollo di SrcSrv (`srcsrv.dll`). Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per altre informazioni sull'installazione di SrcSrv, vedere la documentazione relativa agli Strumenti di debug per Windows. Inoltre, vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Poiché la lettura dei file PDB può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.  
  
 **Visualizza origine server i messaggi diagnostici nella finestra di Output**  
 Quando è attivato il supporto per il server di origine, questa opzione attiva la visualizzazione dei messaggi di diagnostica.  
  
 **Consenti server origine per assembly parzialmente attendibili (solo gestito)**  
 Quando il supporto del server di origine è abilitato, questa impostazione esegue l'override del comportamento predefinito che non recupera le origini per gli assembly parzialmente attendibili.  
  
 **Evidenzia intera riga per i punti di interruzione e l'istruzione corrente**  
 Quando il debugger evidenzia un punto di interruzione o l'istruzione corrente, estende l'evidenziazione all'intera riga.  
  
 **Richiedi file di origine in modo che corrisponda esattamente alla versione originale**  
 Indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile sottoposto a debug. Se la versione non corrisponde, verrà chiesto di cercare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug.  
  
 **Reindirizza tutto il testo di finestra di Output nella finestra controllo immediata**  
 Invia alla finestra **Controllo immediato** tutti i messaggi del debugger che normalmente verrebbero visualizzati nella finestra **Output**.  
  
 **Mostra struttura non elaborata degli oggetti nelle finestre delle variabili**  
 Disattiva tutte le personalizzazioni di visualizzazione della struttura degli oggetti. Per altre informazioni sulla personalizzazione delle visualizzazioni, vedere [creare viste personalizzate di oggetti gestiti](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Disattiva l'ottimizzazione JIT al caricamento del modulo (solo gestito)**  
 Disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato al momento della connessione al debugger. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code").  
  
 **Avvisa se non vi sono simboli all'avvio (solo nativo)**  
 Visualizza una finestra di dialogo di avviso ogni volta che si prova a eseguire il debug di un programma per il quale il debugger non ha informazioni sui simboli.  
  
 **Avvisa se il debug degli script è disabilitato all'avvio**  
 Visualizza una finestra di dialogo di avviso ogni volta che il debugger viene avviato con il debug degli script disabilitato.  
  
 **Carica esportazioni dll**  
 Carica le tabelle di esportazione DLL. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.  
  
 Per visualizzare i simboli disponibili nella tabella di esportazione di una DLL, usare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports`, è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Mostra diagramma di stack in parallelo dal basso in alto**  
 Controlla la direzione in cui vengono visualizzati gli stack nella finestra **Stack in parallelo**.  
  
 **Ignora eccezioni di accesso a memoria GPU se i dati scritti non hanno modificato il valore**  
 Ignora le race condition rilevate durante il debug se i dati non sono stati modificati. Per altre informazioni, vedere [debug del codice GPU](../debugger/debugging-gpu-code.md).  
  
 **Usare la modalità di compatibilità gestita**  
 Sostituisce il motore di debug predefinito con una versione legacy per abilitare gli scenari seguenti:  
  
- Si utilizza un linguaggio .NET Framework diverso da C#, VB o F# che fornisce il proprio analizzatore di espressioni (questo include C++/CLI).  
  
- Si vuole abilitare Modifica e continuazione per i progetti C++ durante il debug in modalità mista.  
  
  Si noti che scegliendo la modalità di compatibilità gestita vengono disabilitate alcune funzionalità implementate solo nel motore di debug predefinito.  
  
  **Usare la modalità di compatibilità nativa**  
  Quando questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.  
  
  Usare questa opzione quando si esegue il debug di codice C++ .NET perché il nuovo motore di debug non supporta la valutazione delle espressioni C++ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non contiene molti dei visualizzatori per i tipi incorporati, ad esempio `std::string` nei progetti di Visual Studio 2015.   Per un'esperienza di debug ottimale, in questi casi usare i progetti di Visual Studio 2013.  
  
  **Usa gli analizzatori di espressioni c# e VB legacy**  
  Il debugger userà gli analizzatori di espressioni di Visual Studio 2013 C#/VB anziché quelli basati su Visual Studio 2015 Roslyn.  
  
  **Avvisa quando si usano visualizzatori di debugger personalizzati processi potenzialmente non sicuri (solo gestito)**  
  Visual Studio genera avvisi quando si usa un visualizzatore di debugger personalizzato che esegue codice nel processo oggetto del debug perché potrebbe essere in esecuzione codice unsafe.  
  
  **Abilita l'allocatore di heap di debug Windows (solo nativo)**  
  Consente all'heap per il debug di Windows di migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.  
  
  **Abilita strumenti di debug per XAML dell'interfaccia utente**  
  Le finestre Albero elementi visivi attivi e Esplora proprietà attive vengono visualizzate quando si avvia il debug (F5) di un tipo di progetto supportato. Per altre informazioni, vedere [delle proprietà di ispezionare XAML durante il debug](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Anteprima degli elementi selezionati in albero elementi visivi attivi**  
  Anche l'elemento XAML di cui è selezionato il contesto viene selezionato nella finestra **Struttura ad albero visuale** attiva.  
  
  **Mostra strumenti di runtime nell'applicazione**  
  Viene illustrato il **albero elementi visivi attivi** comandi in una barra degli strumenti nella finestra principale dell'applicazione XAML in fase di debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2.  
  
  **Abilita strumenti di diagnostica durante il debug**  
  Durante il debug viene visualizzata la finestra **Strumenti di diagnostica**. Per altre informazioni, vedere [integrati nel Debugger profilatura](/visualstudio/profiling/running-profiling-tools-with-or-without-the-debugger).  
  
  **Mostra il perftip relativo al tempo trascorso durante il debug**  
  La finestra di codice mostra il tempo trascorso di una specifica chiamata al metodo quando si esegue il debug.  
  
  **Abilita modifica e continuazione**  
  È possibile usare la funzionalità Modifica e continuazione durante il debug.  
  
  **Abilitare nativa modifica e continuazione**  
  È possibile usare la funzionalità Modifica e continuazione durante il debug del codice C++ nativo. Per altre informazioni, vedere [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Applica le modifiche durante la continuazione (solo nativo)**  
  Visual Studio compila e applica automaticamente le modifiche di codice in sospeso apportate quando il processo viene ripreso da uno stato di interruzione. Se non è selezionato, è possibile scegliere di applicare le modifiche usando l'elemento "Applica modifiche del codice" nel menu Debug.  
  
  **Avvisa in caso di codice non aggiornato (solo nativo)**  
  Consente di ricevere avvisi relativi al codice non aggiornato.  
  
  **Consenti precompilazione (solo nativo)**  
  La precompilazione è consentita.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)
