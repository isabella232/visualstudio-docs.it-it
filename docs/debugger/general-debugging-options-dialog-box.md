---
title: Generale, Debug, finestra di dialogo Opzioni | Microsoft Docs
description: Impostare Visual Studio del debugger per soddisfare le esigenze di debug. È possibile configurare il comportamento di interruzione, i livelli di debug, il comportamento di visualizzazione e molto altro.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b72d97d1300a0745270976afcc0a04e163bac406
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090900"
---
# <a name="general-debugging-options"></a>Opzioni di debug generali

Per impostare Visual Studio opzioni del debugger, selezionare Opzioni strumenti e in Debug selezionare o deselezionare le  >  caselle accanto **alle opzioni**  Generale. È possibile ripristinare tutte le impostazioni predefinite **con** Strumenti  >  **Importa/Esporta Impostazioni** Reimposta tutte le  >  **impostazioni**. Per reimpostare un subset di impostazioni, salvare le impostazioni con l'Importazione/Esportazione guidata **Impostazioni** prima di apportare le modifiche da testare, quindi importare le impostazioni salvate in un secondo momento.

È possibile impostare le opzioni **generali** seguenti:

**Chiedi conferma prima di eliminare tutti i punti di interruzione:** richiede la conferma prima di completare il **comando Elimina tutti i punti di** interruzione.

**Interrompi tutti i processi** quando un processo si interrompe: interrompe simultaneamente tutti i processi a cui è collegato il debugger, quando si verifica un'interruzione.

Interrompi quando le eccezioni superano i limiti appDomain o gestiti/nativi: nel debug gestito o in modalità mista, Common Language Runtime può rilevare le eccezioni che superano i limiti del dominio applicazione o i limiti **gestiti/nativi** quando si verificano le condizioni seguenti:

1. Quando il codice nativo chiama il codice gestito usando l'interoperabilità COM e il codice gestito genera un'eccezione. Vedere [Introduzione all'interoperabilità COM.](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop)

2. Quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito presente nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Vedere [Programmazione con i domini applicazione](/dotnet/articles/framework/app-domains/index).

3. Quando il codice chiama una funzione tramite reflection e tale funzione genera un'eccezione. Vedere [Reflection.](/dotnet/framework/reflection-and-codedom/reflection)

Nelle condizioni 2 e 3, l'eccezione viene talvolta rilevata dal codice gestito in `mscorlib` anziché da Common Language Runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.

**Abilita debug a livello** di indirizzo: abilita le funzionalità avanzate per  il debug a livello di indirizzo (finestra **Disassembly,** finestra Registri e punti di interruzione degli indirizzi).

- **Mostra disassembly se l'origine non** è disponibile: visualizza automaticamente la **finestra Disassembly** quando si esegue il debug di codice per cui l'origine non è disponibile.

**Abilita filtri dei punti** di interruzione: consente di impostare filtri sui punti di interruzione in modo che influiscano solo su processi, thread o computer specifici.

**Usare il nuovo helper eccezioni:** abilita l'helper eccezioni che sostituisce l'assistente eccezioni. L'helper eccezioni è supportato a partire Visual Studio 2017)

> [!NOTE]
> Per il codice gestito, questa opzione è stata precedentemente denominata **Abilita l'assistente eccezioni.**

**Abilita Just My Code:** il debugger visualizza ed esegue solo istruzioni nel codice utente ("My Code"), ignorando il codice di sistema e altro codice ottimizzato o che non dispone di simboli di debug.

- Avvisa se all'avvio non è presente codice utente **(solo gestito):** quando il debug viene avviato con Just My Code abilitato, questa opzione avvisa se non è presente alcun codice utente ("My Code").

**Abilita .NET Framework'istruzione all'origine:** consente al debugger di eseguire un'istruzione .NET Framework'origine. L'abilitazione di questa opzione Just My Code. .NET Framework i simboli verranno scaricati in un percorso della cache. Modificare il percorso della cache con la **finestra di** dialogo Opzioni, **categoria Debug,** **pagina** Simboli.

**Eseguire un'istruzione/istruzione su proprietà** e operatori (solo gestito): impedisce al debugger di eseguire le istruzioni nelle proprietà e negli operatori nel codice gestito.

**Abilita valutazione proprietà e altre chiamate di funzione implicite:** attiva la valutazione automatica delle proprietà e delle chiamate di funzione implicite nelle finestre variabili e nella finestra di **dialogo** Controllo immediato.

- Chiamare la funzione di conversione di stringhe sugli oggetti nelle finestre delle variabili **(solo C# e JavaScript):** esegue una chiamata di conversione di stringa implicita durante la valutazione di oggetti nelle finestre delle variabili. Il risultato viene visualizzato come stringa anziché come nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sostituita dall'attributo DebuggerDisplay (vedere [Uso dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Abilita supporto server di origine:** indica Visual Studio debugger di ottenere i file di origine dai server di origine che implementano il protocollo SrcSrv ( `srcsrv.dll` ). Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per altre informazioni sull'installazione di SrcSrv, vedere la [documentazione di SrcSrv.](/windows-hardware/drivers/debugger/srcsrv) Vedere anche Specificare [i file di simboli (con estensione pdb) e di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

> [!IMPORTANT]
> Poiché la lettura dei file *PDB* può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.

- **Stampa i messaggi di diagnostica del server di origine nella** finestra Output: quando il supporto del server di origine è abilitato, questa impostazione attiva la visualizzazione diagnostica.

- Consenti server di origine per assembly parzialmente attendibili **(solo gestito):** quando il supporto del server di origine è abilitato, questa impostazione sostituisce il comportamento predefinito di non recupero delle origini per gli assembly parzialmente attendibili.

- **Esegui sempre comandi del server** di origine non attendibili senza chiedere conferma: quando il supporto del server di origine è abilitato, questa impostazione sostituisce il comportamento predefinito della richiesta di conferma quando si esegue un comando non attendibile.

**Abilita supporto collegamento all'origine:** indica Visual Studio debugger di scaricare i file di origine per i file con estensione *pdb* che contengono informazioni sul collegamento all'origine. Per altre informazioni sul collegamento all'origine, vedere la [specifica del collegamento all'origine](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Poiché il collegamento all'origine scaricherà i file usando http o https, assicurarsi di considerare attendibile il file *con estensione pdb.*

- **Eseguire il** fall back all'autenticazione di Git Gestione credenziali per tutte le richieste di collegamento all'origine: quando il supporto del collegamento all'origine è abilitato e l'autenticazione di una richiesta di collegamento all'origine ha esito negativo, Visual Studio chiama git Gestione credenziali.

Evidenzia l'intera riga di origine per i punti di interruzione e l'istruzione corrente **(solo C++):** quando il debugger evidenzia un punto di interruzione o un'istruzione corrente, viene evidenziata l'intera riga.

**Richiedi che i file di origine** corrispondano esattamente alla versione originale: indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente usata per compilare l'eseguibile di cui si esegue il debug. Quando la versione non corrisponde, viene richiesto di trovare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug.

**Reindirizza tutto** il testo della finestra di output alla finestra di controllo immediato : invia invece tutti i messaggi del debugger che normalmente verrebbero visualizzati nella finestra **di** output alla **finestra di** controllo immediato.

**Mostra struttura non elaborata degli oggetti nelle finestre delle variabili:** disattiva tutte le personalizzazioni della visualizzazione della struttura degli oggetti. Per altre informazioni sulle personalizzazioni delle visualizzazioni, vedere [Creare visualizzazioni personalizzate di oggetti gestiti.](../debugger/create-custom-views-of-managed-objects.md)

**Non visualizzare l'ottimizzazione JIT** al caricamento del modulo (solo gestito): disabilita l'ottimizzazione JIT del codice gestito quando viene caricato un modulo e viene compilato JIT mentre il debugger è collegato. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code"). Per altre informazioni, vedere [Ottimizzazione e debug JIT.](../debugger/jit-optimization-and-debugging.md)

**Abilita il debug JavaScript per ASP.NET (Chrome, Microsoft Edge e IE):** abilita il debugger di script per ASP.NET app. Al primo uso in Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni di Chrome installate. Disabilitare questa opzione per ripristinare il comportamento legacy.

::: moniker range=">= vs-2019"
**Abilitare l'uso del debugger JavaScript multi-destinazione per il debug di JavaScript nelle** destinazioni applicabili (richiede il riavvio del debug) Abilita la connessione al browser e al back-end contemporaneamente, consentendo di eseguire il debug del codice in esecuzione nel client e nel server direttamente dall'editor.
::: moniker-end

**Carica esportazioni DLL (solo native):** carica le tabelle di esportazione DLL. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.

Per visualizzare i simboli disponibili nella tabella di esportazione di una DLL, usare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports` , è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostra diagramma stack paralleli dal basso verso** l'alto: controlla la direzione di visualizzazione degli stack nella **finestra Stack in** parallelo.

**Ignora le eccezioni di** accesso alla memoria GPU se i dati scritti non modificano il valore : ignora le race conditions rilevate durante il debug se i dati non sono stati modificate. Per altre informazioni, vedere [Debug del codice GPU.](../debugger/debugging-gpu-code.md)

**Usa modalità di compatibilità gestita:** sostituisce il motore di debug predefinito con una versione legacy per abilitare questi scenari:

- Si usa un linguaggio .NET diverso da C#, Visual Basic o F# che fornisce il proprio analizzatore di espressioni (incluso C++/CLI).

- Si vuole abilitare Modifica e continuazione per i progetti C++ durante il debug in modalità mista.

> [!NOTE]
> La scelta della modalità di compatibilità gestita disabilita alcune funzionalità implementate solo nel motore di debug predefinito. Il motore di debug legacy è stato sostituito Visual Studio 2012.

::: moniker range="vs-2017"
Usare gli analizzatori di espressioni **C#** e VB legacy: il debugger userà gli analizzatori di espressioni Visual Studio 2013 C# o Visual Basic anziché gli analizzatori di espressioni basati su Roslyn di Visual Studio 2015.
::: moniker-end

Avvisa quando si usano visualizzatori del debugger personalizzati per processi potenzialmente non sicuri **(solo gestito):** Visual Studio avvisa l'utente quando si usa un visualizzatore del debugger personalizzato che esegue codice nel processo di cui è stato eseguito il debug, perché potrebbe essere in esecuzione codice non sicuro.

**Abilita Windows allocatore heap di debug (solo nativo):** consente all'heap di debug di Windows di migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.

**Abilitare gli strumenti di debug dell'interfaccia** utente per XAML: le finestre Struttura ad albero visuale attiva e Esplorazione proprietà attiva vengono visualizzate quando si avvia il debug **(F5)** di un tipo di progetto supportato. Per altre informazioni, vedere [Esaminare le proprietà XAML durante il debug.](../xaml-tools/inspect-xaml-properties-while-debugging.md)

- **Anteprima degli elementi selezionati nella struttura ad albero visuale** attiva: l'elemento XAML il cui contesto è selezionato viene selezionato anche nella **finestra Struttura ad albero visuale** attiva.

- **Mostra gli strumenti di runtime** nell'applicazione: mostra i **comandi della** struttura ad albero visuale attiva in una barra degli strumenti nella finestra principale dell'applicazione XAML di cui è in corso il debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2.

- **Abilita Ricaricamento rapido XAML:** consente di usare la funzionalità Ricaricamento rapido XAML con codice XAML quando l'app è in esecuzione. Questa funzionalità in precedenza era denominata "Modifica e continuazione XAML"

::: moniker range=">= vs-2019" 
- **Abilita Just My XAML:** a partire da Visual Studio 2019 versione  16.4, per impostazione predefinita la struttura ad albero visuale attiva mostra solo il codice XAML classificato come codice utente. Se si disabilita questa opzione, tutto il codice XAML generato viene visualizzato nello strumento.

- **Disattivare la modalità di selezione quando viene selezionato un elemento** A partire da Visual Studio 2019 versione 16.4, il pulsante del selettore di elementi della barra degli strumenti in-app **(** Abilita selezione ) si disattiva quando viene selezionato un elemento. Se si disabilita questa opzione, la selezione degli elementi rimane attiva fino a quando non si fa di nuovo clic sul pulsante della barra degli strumenti in-app.

- **Applicare Ricaricamento rapido XAML al salvataggio del documento** A partire Visual Studio 2019 versione 16.6, si Ricaricamento rapido XAML quando si salva il documento.

::: moniker-end

**Abilita Strumenti di diagnostica durante il debug:** la **Strumenti di diagnostica** visualizzata durante il debug.

**Mostra perfTip** tempo trascorso durante il debug: la finestra del codice visualizza il tempo trascorso di una determinata chiamata al metodo durante il debug.

**Abilita Modifica e continuazione:** abilita la funzionalità Modifica e continuazione durante il debug.

- **Abilita Modifica e continuazione nativo:** è possibile usare la funzionalità Modifica e continuazione durante il debug del codice C++ nativo. Per altre informazioni, vedere [Modifica e continuazione (C++).](../debugger/edit-and-continue-visual-cpp.md)

- **Applica modifiche alla continuazione (solo nativo):** Visual Studio compila automaticamente e applica tutte le modifiche in sospeso apportate al codice quando si continua il processo da uno stato di interruzione. Se non è selezionata, è possibile scegliere di applicare le modifiche usando la **voce Applica modifiche al** codice nel menu **Debug.**

- **Avvisa in base a codice non obsoleto (solo nativo):** consente di ottenere avvisi relativi a codice non obsoleto.

**Mostra pulsante Esegui fino alla riga selezionata nell'editor** durante il debug: quando questa opzione è selezionata, [durante](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) il debug verrà visualizzato il pulsante Esegui fino alla riga selezionata.

**Chiudi automaticamente la console all'arresto del** debug: Visual Studio di chiudere la console al termine di una sessione di debug.

::: moniker range=">= vs-2019"
**Abilita valutazione rapida delle espressioni (solo gestito):** consente al debugger di tentare una valutazione più veloce simulando l'esecuzione di proprietà e metodi semplici.

**Caricare i simboli di debug in un processo esterno (solo nativo)** Abilita questa [ottimizzazione della memoria durante](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) il debug.

**Portare Visual Studio in primo piano durante l'interruzione nel debugger** Passa Visual Studio in primo piano quando si sospende il debugger.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opzioni disponibili nelle versioni precedenti di Visual Studio

Se si usa una versione precedente di Visual Studio, potrebbero essere presenti alcune opzioni aggiuntive.

**Abilita Edge Strumenti di sviluppo per le app JavaScript UWP (sperimentali):** abilita gli strumenti di sviluppo per le app JavaScript UWP in Microsoft Edge.

**Abilita debugger JavaScript chrome legacy per ASP.NET:** abilita il debugger di script JavaScript di Chrome legacy per ASP.NET app. Al primo uso in Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni di Chrome installate.

**Abilitare l'assistente eccezioni:** per il codice gestito abilita l'assistente eccezioni. A partire da Visual Studio 2017, l'helper eccezioni ha sostituito l'assistente eccezioni.

**Rimuovere lo stack di chiamate** in eccezioni  non gestite: fa in modo che la finestra Stack di chiamate eseere il rollback dello stack di chiamate al punto prima che si sia verificata l'eccezione non gestita.

**Usare un modo sperimentale** per avviare il debug JavaScript di Chrome quando si esegue Visual Studio come amministratore: indica a Visual Studio di provare un nuovo modo per avviare Chrome durante il debug di JavaScript.

**Avvisa se all'avvio** non sono presenti simboli (solo nativo): visualizza una finestra di dialogo di avviso quando si esegue il debug di un programma per il quale il debugger non dispone di informazioni sui simboli.

**Avvisa se il debug degli script è disabilitato all'avvio:** visualizza una finestra di dialogo di avviso quando il debugger viene avviato con il debug degli script disabilitato.

**Usa modalità di** compatibilità nativa: quando questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.

- Usare questa opzione quando si esegue il debug del codice C++ .NET, perché il nuovo motore di debug non supporta la valutazione delle espressioni C++ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non dispone di molti visualizzatori per i tipi predefiniti come `std::string` nei Visual Studio 2015.   Usare Visual Studio 2013 progetti per un'esperienza di debug ottimale in questi casi.

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
