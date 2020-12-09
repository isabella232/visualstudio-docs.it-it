---
title: Generale, debug, finestra di dialogo Opzioni | Microsoft Docs
description: Impostare le opzioni del debugger di Visual Studio per soddisfare le esigenze di debug. È possibile configurare il comportamento delle interruzioni, i livelli di debug, il comportamento di visualizzazione e altro ancora.
ms.custom: SEO-VS-2020
ms.date: 06/04/2020
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
ms.openlocfilehash: 1b052c2cce3d396debb4fbaf8ce688ede3effb98
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863010"
---
# <a name="general-debugging-options"></a>Opzioni generali di debug

Per impostare le opzioni del debugger di Visual Studio, selezionare **strumenti**  >  **Opzioni** e in **debug** selezionare o deselezionare le caselle accanto alle opzioni **generali** . È possibile ripristinare tutte le impostazioni predefinite con **strumenti**  >  **Importa/Esporta impostazioni**  >  **Reimposta tutte le impostazioni**. Per reimpostare un subset di impostazioni, salvare le impostazioni con l' **importazione/esportazione guidata delle impostazioni** prima di apportare le modifiche desiderate, quindi importare le impostazioni salvate in seguito.

È possibile impostare le opzioni **generali** seguenti:

**Chiedi prima di eliminare tutti** i punti di interruzione: richiede la conferma prima di completare il comando **Elimina tutti** i punti di interruzione.

**Interrompi tutti i processi quando si interrompe un processo**: interrompe contemporaneamente tutti i processi a cui è collegato il debugger, quando si verifica un'interruzione.

**Interrompi quando le eccezioni superano AppDomain o i limiti gestiti/nativi**: nel debug in modalità gestita o mista, il Common Language Runtime può rilevare eccezioni che superano i limiti del dominio applicazione o i limiti gestiti/nativi quando vengono soddisfatte le condizioni seguenti:

1. Quando il codice nativo chiama il codice gestito usando l'interoperabilità COM e il codice gestito genera un'eccezione. Vedere [Introduzione all'interoperabilità COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito presente nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Vedere [Programmazione con i domini applicazione](/dotnet/articles/framework/app-domains/index).

3. Quando il codice chiama una funzione tramite reflection e la funzione genera un'eccezione. Vedere [Reflection](/dotnet/framework/reflection-and-codedom/reflection).

Nelle condizioni 2 e 3 l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` anziché dal Common Language Runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.

**Abilita debug a livello di indirizzo**: Abilita le funzionalità avanzate per il debug a livello di indirizzo (finestra **Disassembly** , finestra **registri** e punti di interruzione).

- **Mostra disassembly se l'origine non è disponibile**: Mostra automaticamente la finestra **Disassembly** quando si esegue il debug del codice per cui l'origine non è disponibile.

**Enable breakpoint filters**: consente di impostare i filtri sui punti di interruzione in modo che abbiano effetto solo su processi, thread o computer specifici.

**Usa il nuovo Helper eccezioni**: Abilita l'helper eccezioni che sostituisce le informazioni sulle eccezioni. (L'helper eccezioni è supportato a partire da Visual Studio 2017)

> [!NOTE]
> Per il codice gestito, questa opzione è stata precedentemente denominata **Abilita informazioni sulle eccezioni** .

**Enable Just My Code**: il debugger visualizza ed esegue solo il codice utente ("My Code"), ignorando il codice di sistema e altro codice ottimizzato o privo di simboli di debug.

- **Avvisa se nessun codice utente all'avvio (solo gestito)**: quando il debug inizia con Just My Code abilitato, questa opzione avvisa l'utente se non è presente codice utente ("My Code").

**Abilita .NET Framework esecuzione dell'origine**: consente al debugger di eseguire un'istruzione .NET Framework origine. L'abilitazione di questa opzione Disabilita automaticamente Just My Code. .NET Framework simboli verranno scaricati in un percorso della cache. Modificare il percorso della cache con la finestra di dialogo **Opzioni** , categoria **debug** , pagina **simboli** .

**Esegui istruzione/routine di proprietà e operatori (solo gestito)**: impedisce al debugger di eseguire istruzioni su proprietà e operatori nel codice gestito.

**Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**: attiva la valutazione automatica delle proprietà e delle chiamate di funzione implicite nelle finestre delle variabili e nella finestra di dialogo controllo **immediato** .

- **Chiama la funzione di conversione delle stringhe su oggetti nelle finestre delle variabili (solo C# e JavaScript)**: esegue una chiamata di conversione di stringa implicita durante la valutazione di oggetti nelle finestre delle variabili. Il risultato viene visualizzato come stringa anziché come nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sottoposta a override dall'attributo DebuggerDisplay (vedere [uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Abilita supporto del server di origine**: indica al debugger di Visual Studio di ottenere i file di origine dai server di origine che implementano il protocollo SrcSrv ( `srcsrv.dll` ). Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per ulteriori informazioni sull'installazione di SrcSrv, vedere la documentazione di [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) . Vedere inoltre [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Poiché la lettura dei file *PDB* può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.

- **Stampa messaggi di diagnostica del server di origine nella finestra di output**: quando il supporto del server di origine è abilitato, questa impostazione attiva la visualizzazione di diagnostica.

- **Consenti il server di origine per gli assembly parzialmente attendibili (solo gestito)**: quando è abilitato il supporto del server di origine, questa impostazione sostituisce il comportamento predefinito di non recuperare le origini per gli assembly parzialmente attendibili.

- **Esegui sempre comandi del server di origine non attendibili senza chiedere conferma**: quando il supporto del server di origine è abilitato, questa impostazione sostituisce il comportamento predefinito della richiesta quando si esegue un comando non attendibile.

**Abilita supporto** per il collegamento all'origine: indica al debugger di Visual Studio di scaricare i file di origine per i file con *estensione PDB* contenenti informazioni sul collegamento all'origine. Per ulteriori informazioni sul collegamento di origine, vedere la [specifica del collegamento all'origine](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Poiché il collegamento all'origine scaricherà i file tramite http o HTTPS, assicurarsi di considerare attendibile il file con *estensione PDB* .

- **Eseguire il fallback all'autenticazione di gestione credenziali git per tutte le richieste di collegamento** all'origine: quando è abilitato il supporto per il collegamento all'origine e una richiesta di collegamento di origine non riesce, Visual Studio chiama quindi git Credential Manager.

**Evidenziare intera riga di origine per i punti di interruzione e l'istruzione corrente (solo C++)**: quando il debugger evidenzia un punto di interruzione o l'istruzione corrente, evidenzia l'intera riga.

**Richiedi corrispondenza esatta dei file di origine con la versione originale**: indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile di cui si esegue il debug. Quando la versione non corrisponde, viene richiesto di trovare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug.

**Reindirizza tutto il testo della finestra di output nella finestra di controllo immediato**: Invia tutti i messaggi del debugger che normalmente verrebbero visualizzati nella finestra di **output** nella finestra di **controllo immediato** .

**Mostra struttura non elaborata degli oggetti nelle finestre delle variabili**: Disattiva tutte le personalizzazioni delle visualizzazioni struttura degli oggetti. Per altre informazioni sulle personalizzazioni delle visualizzazioni, vedere [creare visualizzazioni personalizzate di oggetti gestiti](../debugger/create-custom-views-of-managed-objects.md).

**Disattiva l'ottimizzazione JIT al caricamento del modulo (solo gestito)**: Disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato mentre il debugger è collegato. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code"). Per altre informazioni, vedere [debug e ottimizzazione JIT](../debugger/jit-optimization-and-debugging.md).

**Abilita il debug JavaScript per ASP.NET (Chrome, Microsoft Edge e IE)**: Abilita il debugger di script per le app ASP.NET. Al primo uso di Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni Chrome installate. Disabilitare questa opzione per ripristinare il comportamento legacy.

::: moniker range=">= vs-2019"
**Abilitare l'uso del debugger JavaScript multidestinazione per il debug di JavaScript nelle destinazioni applicabili (richiede il riavvio del debug)** Consente la connessione al browser e al back-end simultaneamente, consentendo di eseguire il debug del codice in esecuzione nel client e nel server direttamente dall'editor.
::: moniker-end

**Carica esportazioni DLL (solo nativo)**: carica le tabelle di esportazione DLL. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.

Per visualizzare i simboli disponibili nella tabella di esportazione di una DLL, usare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports` , è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostra il diagramma degli stack in parallelo dal basso** verso l'alto: controlla la direzione in cui vengono visualizzati gli stack nella finestra **stack in parallelo** .

**Ignora le eccezioni di accesso alla memoria GPU se i dati scritti non hanno modificato il valore**: ignora le race condition rilevate durante il debug se i dati non sono stati modificati. Per altre informazioni, vedere [debug del codice GPU](../debugger/debugging-gpu-code.md).

**Usa modalità di compatibilità gestita**: sostituisce il motore di debug predefinito con una versione legacy per abilitare questi scenari:

- Si usa un linguaggio .NET diverso da C#, Visual Basic o F # che fornisce il proprio analizzatore di espressioni (incluso C++/CLI).

- Si vuole abilitare modifica e continuazione per i progetti C++ durante il debug in modalità mista.

> [!NOTE]
> La scelta della modalità di compatibilità gestita Disabilita alcune funzionalità implementate solo nel motore di debug predefinito. Il motore di debug legacy è stato sostituito in Visual Studio 2012.

::: moniker range="vs-2017"
**Usare gli analizzatori di espressioni c# e VB legacy**: il debugger userà gli analizzatori di espressioni Visual Studio 2013 c# o Visual Basic invece degli analizzatori di espressioni basati su Roslyn di Visual Studio 2015.
::: moniker-end

**Avvisa quando si usano i visualizzatori del debugger personalizzati in caso di processi potenzialmente non sicuri (solo gestito)**: Visual Studio avvisa l'utente quando si usa un visualizzatore del debugger personalizzato che esegue il codice nel processo sottoposto a debug, perché potrebbe eseguire codice unsafe.

**Abilita allocatore heap di debug Windows (solo nativo)**: consente all'heap di debug di Windows di migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.

**Abilita strumenti di debug dell'interfaccia utente per XAML**: le finestre albero elementi visivi attivi e Esplora proprietà attive vengono visualizzate quando si avvia il debug (**F5**) di un tipo di progetto supportato. Per altre informazioni, vedere [controllare le proprietà XAML durante il debug](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Anteprima degli elementi selezionati in struttura ad albero visuale** attiva: l'elemento XAML di cui è selezionato il contesto è selezionato anche nella finestra **albero elementi visivi attivi** .

- **Mostra gli strumenti di runtime nell'applicazione**: Mostra i comandi della **struttura ad albero visuale** attiva in una barra degli strumenti nella finestra principale dell'applicazione XAML di cui è in corso il debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2.

- **Abilita ricaricamento attivo XAML**: consente di usare la funzionalità di ricaricamento a caldo di XAML con codice XAML quando l'app è in esecuzione. Questa funzionalità era in precedenza denominata "modifica e continuazione XAML".

::: moniker range=">= vs-2019" 
- **Abilita Just My XAML**: a partire da visual studio 2019 versione 16,4, per impostazione predefinita l' **albero elementi visivi attivi** Mostra solo il codice XAML classificato come codice utente. Se si disabilita questa opzione, tutto il codice XAML generato verrà visualizzato nello strumento.

- **Disattiva la modalità di selezione quando viene selezionato un elemento** A partire da Visual Studio 2019 versione 16,4, il pulsante di selezione dell'elemento della barra degli strumenti in-app (**Abilita selezione**) si disattiva quando viene selezionato un elemento. Se si disabilita questa opzione, la selezione degli elementi resta attiva fino a quando non si fa nuovamente clic sul pulsante della barra degli strumenti in-app.

- **Applicare il ricaricamento a caldo di XAML al salvataggio del documento** A partire da Visual Studio 2019 versione 16,6, applica il ricaricamento a caldo di XAML quando si salva il documento.

::: moniker-end

**Abilita strumenti di diagnostica durante il debug**: la finestra **strumenti di diagnostica** viene visualizzata durante il debug.

**Mostra tempo trascorso perftip relativo al durante il debug**: la finestra del codice Visualizza il tempo trascorso di una determinata chiamata al metodo durante il debug.

**Abilita modifica e continuazione**: Abilita la funzionalità modifica e continuazione durante il debug.

- **Abilita modifica e continuazione nativa**: è possibile usare la funzionalità modifica e continuazione durante il debug del codice C++ nativo. Per ulteriori informazioni, vedere [modifica e continuazione (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Applica le modifiche durante la continuazione (solo nativo)**: Visual Studio compila e applica automaticamente eventuali modifiche al codice in sospeso apportate quando si continua il processo da uno stato di interruzione. Se questa opzione non è selezionata, è possibile scegliere di applicare le modifiche utilizzando l'elemento **Applica modifiche al codice** nel menu **debug** .

- **Avvisa in caso di codice non aggiornato (solo nativo)**: ricevere avvisi sul codice non aggiornato.

**Mostra pulsante Esegui fino al clic nell'editor durante il debug**: se questa opzione è selezionata, il pulsante [Esegui fino al clic](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) verrà visualizzato durante il debug.

**Chiude automaticamente la console quando il debug viene interrotto**: indica a Visual Studio di chiudere la console alla fine di una sessione di debug.

::: moniker range=">= vs-2019"
**Abilita valutazione rapida delle espressioni (solo gestito)**: consente al debugger di provare più velocemente la valutazione simulando l'esecuzione di semplici metodi e proprietà.

**Carica i simboli di debug nel processo esterno (solo nativo)** Abilita questa [ottimizzazione](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) per la memoria durante il debug.

**Portare Visual Studio in primo piano quando si verificano interruzioni nel debugger** Passa a Visual Studio in primo piano durante la pausa nel debugger.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opzioni disponibili nelle versioni precedenti di Visual Studio

Se si usa una versione precedente di Visual Studio, potrebbero essere presenti alcune opzioni aggiuntive.

**Abilita strumenti di sviluppo Edge per le app UWP JavaScript (sperimentale)**: Abilita gli strumenti di sviluppo per le app JavaScript UWP in Microsoft Edge.

**Abilita il debugger JavaScript legacy di Chrome per ASP.NET**: Abilita il debugger di script JavaScript di Chrome legacy per le app ASP.NET. Al primo uso di Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni Chrome installate.

**Abilitazione di informazioni sulle eccezioni**: per il codice gestito, Abilita le informazioni sulle eccezioni. A partire da Visual Studio 2017, l'helper eccezioni ha sostituito le informazioni sulle eccezioni.

**Rimuovi stack di chiamate su eccezioni non gestite**: determina il rollback dello stack di chiamate da parte della finestra **stack** di chiamate al punto precedente l'eccezione non gestita.

**Usare il metodo sperimentale per avviare il debug JavaScript di Chrome quando si esegue Visual Studio come amministratore**: indica a Visual Studio di provare un nuovo modo per avviare Chrome durante il debug di JavaScript.

**Avvisa se non ci sono simboli all'avvio (solo nativo)**: Visualizza una finestra di dialogo di avviso quando si esegue il debug di un programma per il quale il debugger non ha informazioni sui simboli.

**Avvisa se il debug degli script è disabilitato all'avvio**: Visualizza una finestra di dialogo di avviso quando il debugger viene avviato con il debug degli script disabilitato.

**Usa modalità di compatibilità nativa**: se questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.

- Usare questa opzione quando si esegue il debug del codice .NET C++, perché il nuovo motore di debug non supporta la valutazione delle espressioni C++ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Il motore legacy, ad esempio, non dispone di molti visualizzatori per i tipi incorporati come `std::string` nei progetti di Visual Studio 2015.   In questi casi, utilizzare Visual Studio 2013 progetti per un'esperienza di debug ottimale.

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
