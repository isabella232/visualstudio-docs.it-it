---
title: Generale, debug, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/09/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8579504f549cb078fee178127c7396896fce5313
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399416"
---
# <a name="general-debugging-options"></a>Opzioni di debug generali

Per impostare le opzioni del debugger di Visual Studio, selezionare **Tools** > **opzioni**, quindi in **debug** selezionare o deselezionare le caselle accanto al  **Generale** opzioni. È possibile ripristinare tutte le impostazioni predefinite **degli strumenti** > **Importa / Esporta impostazioni** > **Reimposta tutte le impostazioni**. Per reimpostare un sottoinsieme delle impostazioni, salvare le impostazioni con la **importazione / esportazione guidata delle impostazioni** prima di apportare le modifiche che si vuole testare, quindi importare le impostazioni salvate in un secondo momento.

È possibile impostare quanto segue **generale** opzioni:

**Chiedi prima di eliminare tutti i punti di interruzione**: Richiede conferma prima dell'esecuzione del comando **Elimina tutti i punti di interruzione**.

**Quando si interrompe un processo, interrompi tutti i processi**: Interrompe simultaneamente tutti i processi a cui è connesso il debugger quando si verifica un'interruzione.

**Interrompi quando le eccezioni superano il dominio applicazione o i limiti gestiti/nativi**: Durante il debug in modalità gestita o mista, Common Language Runtime è in grado di rilevare eccezioni che superano i limiti del dominio applicazione o i limiti gestiti/nativi quando sono vere le seguenti condizioni:

1. Quando il codice nativo chiama il codice gestito usando l'interoperabilità COM e il codice gestito genera un'eccezione. Visualizzare [Introduzione all'interoperabilità COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito presente nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Vedere [Programmazione con i domini applicazione](/dotnet/articles/framework/app-domains/index).

3. Quando il codice chiama una funzione tramite reflection e che funzione genera un'eccezione. Visualizzare [Reflection](/dotnet/framework/reflection-and-codedom/reflection).

Nelle condizioni di 2 e 3, l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` anziché da common language runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.

**Abilita debug a livello di indirizzo**: Abilita le funzionalità avanzate per il debug a livello di indirizzo (finestra **Disassembly**, finestra **Registri** e punti di interruzione).

- **Mostra disassembly se l'origine non è disponibile**:   Mostra automaticamente il **Disassembly** finestra durante il debug di codice per cui l'origine è disponibile.

**Abilita i filtri dei punti di interruzione**: Consente di applicare filtri ai punti di interruzione in modo che abbiano effetto solo su determinati processi, thread o computer.

**Usa il nuovo Helper eccezioni**: Abilita il supporto di eccezioni che sostituisce le informazioni sulle eccezioni. (Helper eccezioni è supportato a partire da Visual Studio 2017)

> [!NOTE]
> Per codice gestito, questa opzione è stata chiamata precedentemente **Abilita informazioni sulle eccezioni** .

**Abilita Just My Code**: Il debugger visualizza ed esegue solo il codice utente ("My Code"), ignorando il codice di sistema e altro codice ottimizzato o privo di simboli di debug.

- **Avvisa se all'avvio non è presente codice utente (solo gestito)**:   Quando il debug viene avviato con Just My Code attivato, questa opzione determina la visualizzazione di un avviso se non è presente codice utente ("My Code").

**Abilita esecuzione di istruzioni origine .NET Framework**: Consente al debugger di eseguire l'origine di .NET Framework. Attivazione di questa opzione disattiva automaticamente Just My Code. .NET framework simboli verranno scaricati in un percorso della cache. Modificare il percorso della cache con la **le opzioni** della finestra di dialogo **debug** categoria **simboli** pagina.

**Esegui istruzione/routine di proprietà e operatori (solo gestito)**: Impedisce al debugger di eseguire istruzioni di proprietà e operatori nel codice gestito.

**Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**: Attiva la valutazione automatica di proprietà e altre chiamate di funzioni implicite nelle finestre delle variabili e nella finestra di dialogo **Controllo immediato**.

- **Chiama la funzione di conversione delle stringhe su oggetti nelle finestre delle variabili (solo C# e JavaScript)**: Esegue una chiamata di conversione delle stringhe implicita durante la valutazione di oggetti nelle finestre delle variabili. Il risultato viene visualizzato come stringa anziché il nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sottoposto a override mediante l'attributo DebuggerDisplay (vedere [usando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Abilita il supporto del server di origine**: Indica al debugger di Visual Studio di ottenere i file di origine da server di origine che implementano il protocollo di SrcSrv (`srcsrv.dll`). Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per altre informazioni sull'installazione di SrcSrv, vedere la [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) documentazione. Inoltre, vedere [specificare i simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Poiché la lettura dei file *PDB* può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.

- **Visualizza i messaggi diagnostici del server di origine nella finestra di output**:   Quando è attivato il supporto per il server di origine, questa opzione attiva la visualizzazione dei messaggi di diagnostica.

- **Consenti server origine per assembly parzialmente attendibili (solo gestito)**:   Quando il supporto del server di origine è abilitato, questa impostazione esegue l'override del comportamento predefinito che non recupera le origini per gli assembly parzialmente attendibili.

- **Esegui sempre comandi del server di origine non attendibili senza chiedere conferma**:   Quando è abilitato il supporto del server di origine, questa impostazione esegue l'override del comportamento predefinito di richiesta di conferma quando si esegue un comando non attendibile.

**Abilita il supporto per il collegamento all'origine**: Indica al debugger di Visual Studio per scaricare i file di origine per *PDB* file contenenti informazioni sui collegamenti di origine. Per altre informazioni sul collegamento all'origine, vedere la [specifica l'origine collegamento](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Perché il collegamento all'origine scaricherà i file tramite http o https, assicurarsi che si ritiene attendibile il *PDB* file.

- **Esegui fallback all'autenticazione di Gestione credenziali GIT per tutte le richieste di collegamento all'origine**:   Quando è abilitato il supporto di collegamento all'origine e una richiesta di collegamento all'origine non riesce l'autenticazione, Visual Studio chiama quindi il Git Credential Manager.

**Evidenzia intera riga per i punti di interruzione e l'istruzione corrente (solo C++)**: Quando il debugger evidenzia un punto di interruzione o l'istruzione corrente, estende l'evidenziazione all'intera riga.

**Richiedi corrispondenza esatta dei file di origine con la versione originale**: Indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile sottoposto a debug. Quando la versione non corrisponde, viene chiesto di trovare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug.

**Reindirizza tutto il testo della finestra di output nella finestra di controllo immediato**: Invia alla finestra **Controllo immediato** tutti i messaggi del debugger che normalmente verrebbero visualizzati nella finestra **Output**.

**Mostra struttura non elaborata degli oggetti nelle finestre delle variabili**: Disattiva tutte le personalizzazioni di visualizzazione della struttura degli oggetti. Per altre informazioni sulla personalizzazione delle visualizzazioni, vedere [creare viste personalizzate di oggetti. Managed](../debugger/create-custom-views-of-dot-managed-objects.md).

**Disattiva l'ottimizzazione JIT al caricamento del modulo (solo gestito)**: Disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato al momento della connessione al debugger. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code"). Per altre informazioni, vedere [JIT debug e ottimizzazione](../debugger/jit-optimization-and-debugging.md).

**Abilita il debug JavaScript per ASP.NET (Chrome, Microsoft Edge e Internet Explorer)**: Consente al debugger di script per le app ASP.NET. Al primo utilizzo in Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni Chrome che è stato installato. Disabilitare questa opzione per ripristinare il comportamento legacy.

**Abilita strumenti di sviluppo Edge per app JavaScript per la piattaforma UWP (sperimentale)**: Abilita strumenti di sviluppo per le app UWP JavaScript in Microsoft Edge.

**Abilita il debugger JavaScript legacy di Chrome per ASP.NET**: Consente al debugger di script JavaScript di Chrome legacy per le app ASP.NET. Al primo utilizzo in Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni Chrome che è stato installato.

**Avvia il debug di Chrome JavaScript in modo sperimentale durante l'esecuzione di Visual Studio come amministratore**: Indica a Visual Studio per provare un nuovo modo per avviare Chrome durante il debug di JavaScript.

**Carica esportazioni DLL (solo Nativo)**: Carica le tabelle di esportazione DLL. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.

Per visualizzare i simboli disponibili nella tabella di esportazione di una DLL, usare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports`, è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostra diagramma degli stack in parallelo dal basso verso l'alto**: Controlla la direzione in cui vengono visualizzati gli stack nella finestra **Stack in parallelo**.

**Ignora eccezioni di accesso a memoria GPU se i dati scritti non hanno modificato il valore**: Ignora le race condition rilevate durante il debug se i dati non sono stati modificati. Per altre informazioni, vedere [debug del codice GPU](../debugger/debugging-gpu-code.md).

**Utilizza modalità di compatibilità gestita**: Sostituisce il motore di debug predefinito con una versione legacy per abilitare gli scenari seguenti:

- Si usa un linguaggio di .NET Framework diverso da C#, Visual Basic o F# che fornisce il proprio analizzatore di espressioni (questo include c++ /CLI CLI).

- Si desidera abilitare Modifica e continuazione per i progetti C++ durante il debug in modalità mista.

> [!NOTE]
> Modalità la scelta di compatibilità gestita vengono disabilitate alcune funzionalità implementate solo nel motore di debug predefinito. Il motore di debug legacy è stato sostituito in Visual Studio 2012.

**Usa gli analizzatori di espressioni C# e VB legacy**: Il debugger userà Visual Studio 2013 C# o Visual Basic gli analizzatori di espressioni anziché gli analizzatori di espressioni basate su Visual Studio 2015 Roslyn.

**Avvisa quando si usano visualizzatori di debugger personalizzati in caso di processi potenzialmente non sicuri (solo gestito)**: Visual Studio genera avvisi quando si usa un visualizzatore di debugger personalizzato che esegue codice nel processo oggetto del debug perché potrebbe essere in esecuzione codice unsafe.

**Abilita l'allocatore di heap per il debug di Windows (solo nativo)**: Consente all'heap per il debug di Windows di migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.

**Abilita strumenti di debug dell'interfaccia utente per XAML**: Le finestre Struttura ad albero visuale attiva e Esplora proprietà attive vengono visualizzate quando si avvia il debug (**F5**) di un tipo di progetto supportato. Per altre informazioni, vedere [delle proprietà di ispezionare XAML durante il debug](../debugger/inspect-xaml-properties-while-debugging.md).

- **Anteprima degli elementi selezionati in Struttura ad albero visuale attiva**:   Anche l'elemento XAML di cui è selezionato il contesto viene selezionato nella finestra **Struttura ad albero visuale** attiva.

- **Mostra gli strumenti di runtime nell'applicazione**: Viene illustrato il **albero elementi visivi attivi** comandi in una barra degli strumenti nella finestra principale dell'applicazione XAML in fase di debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2.

- **Abilita Modifica e continuazione XAML**:   Consente di usare la modifica e continuazione funzionalità con il codice XAML.

**Abilita strumenti di diagnostica durante il debug**: Durante il debug viene visualizzata la finestra **Strumenti di diagnostica**.

**Mostra il PerfTip relativo al tempo trascorso durante il debug**: La finestra di codice mostra il tempo trascorso di una specifica chiamata al metodo quando si esegue il debug.

**Abilita Modifica e continuazione**: Abilita la funzionalità Modifica e continuazione durante il debug.

- **Abilita Modifica e continuazione nativo**: È possibile usare la funzionalità Modifica e continuazione durante il debug del codice C++ nativo. Per altre informazioni, vedere [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Applica le modifiche durante la continuazione (solo nativo)**: Visual Studio compila e applica automaticamente le modifiche di codice in sospeso apportate quando il processo viene ripreso da uno stato di interruzione. Se non è selezionato, è possibile scegliere di applicare le modifiche con il comando **Applica modifiche del codice** nel menu **Debug**.

- **Avvisa in caso di codice non aggiornato (solo nativo)**:   Consente di ricevere avvisi relativi al codice non aggiornato.

**Mostra Run a fare clic sul pulsante nell'editor durante il debug**: Quando questa opzione è selezionata, il [Esegui fino al clic](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) pulsante verrà visualizzato durante il debug.

**Chiudi automaticamente la console quando viene arrestato il debug**: Indica a Visual Studio per chiudere la console alla fine di una sessione di debug.

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opzioni disponibili nelle versioni precedenti di Visual Studio

Se si usa una versione precedente di Visual Studio, alcune opzioni aggiuntive potrebbero essere presenti.

**Abilita Informazioni sulle eccezioni**: Per codice gestito, Abilita informazioni sulle eccezioni. A partire da Visual Studio 2017, l'Helper eccezioni sostituito informazioni sulle eccezioni.

**Rimuovi stack di chiamate su eccezioni non gestite**: La finestra **Stack di chiamate** esegue il rollback dello stack di chiamate al punto precedente l'eccezione non gestita.

**Avvisa se non vi sono simboli all'avvio (solo nativo)**: Visualizza una finestra di dialogo di avviso quando si esegue il debug di un programma per il quale il debugger non dispone di alcuna informazione sui simboli.

**Avvisa se il debug degli script è disabilitato all'avvio**: Visualizza una finestra di dialogo di avviso ogni volta che il debugger viene avviato con il debug degli script disabilitato.

**Usa modalità di compatibilità nativa**: Quando questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.

- Usare questa opzione quando si esegue il debug di codice C++ .NET, poiché il nuovo motore di debug non supporta la valutazione delle espressioni C++ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non contiene molti dei visualizzatori per i tipi incorporati, ad esempio `std::string` nei progetti di Visual Studio 2015.   Usare i progetti di Visual Studio 2013 per l'esperienza di debug ottima in questi casi.

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)