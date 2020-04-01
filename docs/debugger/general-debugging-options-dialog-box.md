---
title: Generale, Debug, finestra di dialogo Opzioni Documenti Microsoft
ms.date: 11/12/2019
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
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472692"
---
# <a name="general-debugging-options"></a>Opzioni di debug generali

Per impostare le opzioni del debugger di Visual Studio, selezionare**Opzioni** **degli strumenti** > e in **Debug** selezionare o deselezionare le caselle accanto alle opzioni **generali.** È possibile ripristinare tutte le impostazioni predefinite con **Strumenti** > **Importa ed Esporta impostazioni** > **Ripristina tutte le impostazioni**. Per reimpostare un sottoinsieme di impostazioni, salvare le impostazioni con **l'Importazione/Esportazione guidata impostazioni** prima di apportare le modifiche che si desidera testare, quindi importare le impostazioni salvate in seguito.

È possibile impostare le seguenti opzioni **generali:**

**Chiedi prima di eliminare tutti i punti di interruzione**: Richiede conferma prima di completare il comando Elimina tutti i punti di **interruzione.**

**Interrompi tutti i processi quando si interrompe un processo:** interrompe contemporaneamente tutti i processi a cui è collegato il debugger, quando si verifica un'interruzione.

**Interrompi quando le eccezioni attraversano AppDomain o i limiti gestiti/nativi:** nel debug gestito o in modalità mista, Common Language Runtime può intercettare le eccezioni che superano i limiti del dominio applicazione o i limiti gestiti/nativi quando sono vere le condizioni seguenti:

1. Quando il codice nativo chiama il codice gestito usando l'interoperabilità COM e il codice gestito genera un'eccezione. Vedere [Introduzione all'interoperabilità COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito presente nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Vedere [Programmazione con i domini applicazione](/dotnet/articles/framework/app-domains/index).

3. Quando il codice chiama una funzione tramite reflection e tale funzione genera un'eccezione. Consultate [Riflessione](/dotnet/framework/reflection-and-codedom/reflection).

Nelle condizioni 2 e 3, l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` anziché da Common Language Runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.

**Abilita debug**a livello di indirizzo : Abilita le funzionalità avanzate per il debug a livello di indirizzo (la finestra **Disassembly,** la finestra **Registri** e i punti di interruzione degli indirizzi).

- **Mostra disassembly se l'origine non è disponibile:** mostra automaticamente la finestra **Disassembly** quando si esegue il debug di codice per il quale l'origine non è disponibile.

**Abilita filtri punto di interruzione**: Consente di impostare filtri sui punti di interruzione in modo che influiscano solo su processi, thread o computer specifici.

**Usa il nuovo Exception Helper**: Abilita l'helper eccezioni che sostituisce l'Assistente eccezioni. (Exception Helper è supportato a partire da Visual Studio 2017)

> [!NOTE]
> Per il codice gestito, questa opzione è stata precedentemente denominata **Abilitare l'Assistente eccezioni** .

**Abilita Just My Code**: Il debugger visualizza e entra passo nel codice utente ("My Code") solo, ignorando il codice di sistema e altro codice che è ottimizzato o che non dispone di simboli di debug.

- **Avvisa se nessun codice utente all'avvio (solo gestito):** quando il debug inizia con Just My Code abilitato, questa opzione avvisa se non è presente alcun codice utente ("My Code").

**Abilita esecuzione graduale origine .NET Framework:** consente al debugger di eseguire l'istruzione nell'origine .NET Framework. L'attivazione di questa opzione disabilita automaticamente Just My Code. I simboli di .NET Framework verranno scaricati in un percorso della cache. Modificare il percorso della cache con la finestra di dialogo **Opzioni,** la categoria **Debug,** la pagina **Simboli.**

**Eseguire l'istruzione step over di proprietà e operatori (solo gestito):** impedisce al debugger di eseguire l'esecuzione di proprietà e operatori nel codice gestito.

**Abilita la valutazione**delle proprietà e altre chiamate di funzione implicite: attiva la valutazione automatica delle proprietà e delle chiamate di funzione implicite nelle finestre delle variabili e nella finestra di dialogo **Controllo immediato.**

- Funzione di conversione delle stringhe di chiamata sugli oggetti nelle finestre delle **variabili (solo C , c'è e JavaScript)**: Esegue una chiamata di conversione di stringa implicita durante la valutazione di oggetti nelle finestre delle variabili. Il risultato viene visualizzato come stringa anziché come nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sostituita dall'attributo DebuggerDisplay (vedere [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Abilita supporto server**di origine : Indica al debugger di Visual Studio`srcsrv.dll`di ottenere i file di origine dai server di origine che implementano il protocollo SrcSrv ( ). Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per ulteriori informazioni sull'installazione di SrcSrv, vedere la documentazione di [SrcSrv.](/windows-hardware/drivers/debugger/srcsrv) Vedere inoltre [Specificare i file di simbolo (con estensione pdb) e i file](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)di origine .

> [!IMPORTANT]
> Poiché la lettura dei file *PDB* può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.

- **Stampa messaggi di diagnostica**del server di origine nella finestra Output : quando è abilitato il supporto del server di origine, questa impostazione attiva la visualizzazione diagnostica.

- **Consenti server di origine per assembly parzialmente attendibili (solo gestito):** quando è abilitato il supporto del server di origine, questa impostazione esegue l'override del comportamento predefinito di non recuperare le origini per gli assembly parzialmente attendibili.

- Esegui sempre comandi del server di **origine non attendibili senza chiedere conferma:** quando il supporto del server di origine è abilitato, questa impostazione esegue l'override del comportamento predefinito di richiesta quando si esegue un comando non attendibile.

**Abilita supporto collegamento origine**: Indica al debugger di Visual Studio di scaricare i file di origine per i file *con estensione pdb* che contengono informazioni sul collegamento di origine. Per ulteriori informazioni sul collegamento di origine, vedere la [specifica del collegamento Origine](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Poiché Collegamento origine scaricherà i file utilizzando http o https, assicurarsi di considerare attendibile il file *con estensione pdb.*

- **Eseguire il rollback all'autenticazione**di Git Credential Manager per tutte le richieste di collegamento di origine: quando il supporto del collegamento di origine è abilitato e una richiesta di collegamento di origine non riesce l'autenticazione, Visual Studio chiama Gestione credenziali Git.

**Evidenziare l'intera riga per i punti di interruzione e l'istruzione corrente (solo In C)**: quando il debugger evidenzia un punto di interruzione o un'istruzione corrente, evidenzia l'intera riga.

Richiedi che i file di **origine corrispondano esattamente**alla versione originale: indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile di cui si sta eseguendo il debug. Quando la versione non corrisponde, viene richiesto di trovare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug.

Reindirizza tutto il testo della **finestra di output alla finestra Immediata:** invia tutti i messaggi del debugger che normalmente vengono visualizzati nella finestra **Output** alla finestra **Immediata.**

**Mostra struttura non elaborata degli oggetti nelle finestre delle variabili:** disattiva tutte le personalizzazioni della visualizzazione della struttura di oggetti. Per ulteriori informazioni sulle personalizzazioni delle visualizzazioni, vedere [Creare visualizzazioni personalizzate di oggetti gestiti.](../debugger/create-custom-views-of-managed-objects.md)

**Elimina ottimizzazione JIT al caricamento del modulo (solo gestito)**: disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato mentre il debugger è collegato. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code"). Per ulteriori informazioni, vedere [Ottimizzazione JIT e debug](../debugger/jit-optimization-and-debugging.md).

**Abilita il debug JavaScript per ASP.NET (Chrome, Microsoft Edge e IE):** abilita il debugger di script per le app ASP.NET. Al primo utilizzo in Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni di Chrome installate. Disattivare questa opzione per ripristinare il comportamento legacy.

Abilita gli strumenti di **sviluppo di Edge per le app JavaScript UWP (sperimentale):** abilita gli strumenti di sviluppo per le app JavaScript UWP in Microsoft Edge.

**Abilita il debugger JavaScript Chrome legacy per ASP.NET:** abilita il debugger di script JavaScript Chrome legacy per le app ASP.NET. Al primo utilizzo in Chrome, potrebbe essere necessario accedere al browser per abilitare le estensioni di Chrome installate.

**Utilizzare modo sperimentale per avviare il debug JavaScript di Chrome quando si esegue Visual Studio come amministratore**: Indica a Visual Studio di provare un nuovo modo per avviare Chrome durante il debug JavaScript.

**Carica dll exports (solo nativo):** carica le tabelle di esportazione dll. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.

Per visualizzare i simboli disponibili nella tabella di esportazione di una DLL, usare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports` , è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostra diagrammi di stack paralleli dal basso verso l'alto:** controlla la direzione in cui gli stack vengono visualizzati nella finestra **Stack in parallelo.**

**Ignora le eccezioni di accesso alla memoria GPU se i dati scritti non modificano il valore:** ignora le race condition rilevate durante il debug se i dati non sono stati modificati. Per ulteriori informazioni, vedere [Debug del codice GPU](../debugger/debugging-gpu-code.md).

**Usa modalità compatibilità gestita:** sostituisce il motore di debug predefinito con una versione precedente per abilitare questi scenari:Use Managed Compatibility Mode : Replaces the default debugging engine with a legacy version to enable these scenarios:

- Si sta utilizzando un linguaggio .NET diverso da C , Visual Basic o F , che fornisce il proprio analizzatore di espressioni (questo include c'è/ CLI).

- Durante il debug in modalità mista, si desidera abilitare i progetti di modifica e continuazione per i progetti in c.

> [!NOTE]
> La scelta della modalità di compatibilità gestita disabilita alcune funzionalità implementate solo nel motore di debug predefinito. Il motore di debug legacy è stato sostituito in Visual Studio 2012.

**Utilizzare gli analizzatori**di espressioni legacy di C e VB: il debugger utilizzerà gli analizzatori di espressioni di Visual Studio 2013 o Visual Basic anziché gli analizzatori di espressioni basati su Roslyn di Visual Studio 2015.

Avvisa quando si **utilizzano visualizzatori del debugger personalizzati su processi potenzialmente non sicuri (solo gestiti):** Visual Studio avvisa quando si utilizza un visualizzatore del debugger personalizzato che esegue codice nel processo sottoposto a debug, perché potrebbe essere in esecuzione codice unsafe.

**Abilita allocatore heap di debug di Windows (solo nativo):** consente all'heap di debug di Windows di migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.

Abilita gli strumenti di **debug dell'interfaccia**utente per XAML: le finestre Struttura ad albero visuale attiva e Esplora proprietà dinamiche verranno visualizzate quando si avvia il debug (**F5**) di un tipo di progetto supportato. Per ulteriori informazioni, consultate [Esaminare le proprietà XAML durante il debug.](../xaml-tools/inspect-xaml-properties-while-debugging.md)

- Anteprima degli elementi selezionati nella struttura **ad albero visuale attiva:** l'elemento XAML il cui contesto selezionato viene selezionato anche nella finestra **Albero visuale attivo.**

- Mostra strumenti di **runtime nell'applicazione:** mostra i comandi **della struttura ad albero visuale attiva** in una barra degli strumenti nella finestra principale dell'applicazione XAML di cui viene eseguito il debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2.

- **Abilita ricaricamento automatico XAML:** consente di usare la funzionalità di ricaricamento automatico XAML con codice XAML quando l'app è in esecuzione. (Questa funzionalità era precedentemente chiamata "Modifica e continuazione XAML")

::: moniker range=">= vs-2019" 
- **Abilita Just My XAML:** a partire da Visual Studio 2019 versione 16.4, la struttura **ad albero visuale** attiva per impostazione predefinita mostra solo XAML classificato come codice utente. Se disabiliti questa opzione, tutto il codice XAML generato viene visualizzato nello strumento.

- **Disattivare la modalità di selezione quando viene selezionato un elemento** A partire da Visual Studio 2019 versione 16.4, il pulsante di selezione dell'elemento della barra degli strumenti in-app (**Abilita selezione**) si disattiva quando viene selezionato un elemento. Se disabiliti questa opzione, la selezione dell'elemento rimane attiva fino a quando non fai di nuovo clic sul pulsante della barra degli strumenti in-app.
::: moniker-end

**Abilita strumenti di diagnostica durante il debug**: durante il debug viene visualizzata la finestra Strumenti di **diagnostica.**

**Mostra tempo trascorso PerfTip durante il debug**: La finestra del codice visualizza il tempo trascorso di una determinata chiamata al metodo durante il debug.

**Abilita Modifica e continuazione**: Abilita la funzionalità Modifica e Continuazione durante il debug.

- **Abilita modifica e continuazione nativa**: è possibile utilizzare la funzionalità Modifica e continuazione durante il debug di codice nativo di C. Per ulteriori informazioni, consultate [Modifica e continuazione (C )](../debugger/edit-and-continue-visual-cpp.md).

- **Applica modifiche in continua (solo nativo):** Visual Studio compila automaticamente e applica tutte le modifiche al codice in sospeso apportate durante la continuazione del processo da uno stato di interruzione. Se non è selezionata, è possibile scegliere di applicare le modifiche utilizzando la voce **Applica modifiche codice** nel menu **Debug.**

- **Avvisa in caso di codice non aggiornato (solo nativo):** visualizza avvisi relativi al codice non aggiornato.

**Mostra il pulsante Esegui per fare clic nell'editor durante il debug**: quando questa opzione è selezionata, il pulsante [Esegui fino a fare clic](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) verrà visualizzato durante il debug.

**Chiudi automaticamente la console quando il debug si interrompe:** indica a Visual Studio di chiudere la console al termine di una sessione di debug.

::: moniker range=">= vs-2019"
**Abilita valutazione rapida delle espressioni (solo gestita):** consente al debugger di tentare una valutazione più rapida simulando l'esecuzione di proprietà e metodi semplici.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opzioni disponibili nelle versioni precedenti di Visual StudioOptions available in older versions of Visual Studio

Se si usa una versione precedente di Visual Studio, potrebbero essere presenti alcune opzioni aggiuntive.

**Abilitare l'Assistente eccezioni:** per il codice gestito, abilita l'Assistente eccezioni. A partire da Visual Studio 2017, L'assistente alle eccezioni ha sostituito l'Assistente eccezioni.

Rimozione dello stack di **chiamate su eccezioni non gestite:** fa sì che la finestra **Stack** di chiamate esegua il rollback dello stack di chiamate fino al punto precedente che si verificasse l'eccezione non gestita.

**Avvisa se nessun simbolo all'avvio (solo nativo):** visualizza una finestra di dialogo di avviso quando si esegue il debug di un programma per il quale il debugger non dispone di informazioni sui simboli.

**Avvisa se il debug degli script è disabilitato all'avvio:** visualizza una finestra di dialogo di avviso quando il debugger viene avviato con il debug di script disabilitato.

**Usa modalità compatibilità nativa:** quando questa opzione è selezionata, il debugger utilizza il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.

- Utilizzare questa opzione quando si esegue il debug di codice .NET C, perché il nuovo motore di debug non supporta la valutazione di espressioni .NET C. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non dispone di `std::string` molti visualizzatori per i tipi incorporati, ad esempio nei progetti di Visual Studio 2015.For example, the legacy engine lacks many visualizers for built-in types like in Visual Studio 2015 projects.   Utilizzare i progetti di Visual Studio 2013 per un'esperienza di debug ottimale in questi casi.

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Primo sguardo al debugger](../debugger/debugger-feature-tour.md)
