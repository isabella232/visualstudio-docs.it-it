---
title: Cenni preliminari sul protocollo server di linguaggio | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703111"
---
# <a name="language-server-protocol"></a>Protocollo di server di linguaggio

## <a name="what-is-the-language-server-protocol"></a>Che cos'è il protocollo server del linguaggio?

Il supporto di funzionalità di modifica avanzate, come il completamento automatico del codice sorgente o la **definizione** di un linguaggio di programmazione in un editor o IDE, è tradizionalmente molto complesso e richiede molto tempo. In genere è necessario scrivere un modello di dominio (uno scanner, un parser, un controllo del tipo, un generatore e altro) nel linguaggio di programmazione dell'editor o dell'IDE. Il plug-in Eclipse CDT, che fornisce il supporto per C/C++ nell'IDE di Eclipse, ad esempio, è scritto in Java poiché l'IDE di Eclipse è scritto in Java. Seguendo questo approccio, si significherebbe implementare un modello di dominio C/C++ nel codice TypeScript for Visual Studio e un modello di dominio separato in C# per Visual Studio.

Anche la creazione di modelli di dominio specifici della lingua è molto più semplice se uno strumento di sviluppo può riutilizzare le librerie specifiche del linguaggio esistenti. Tuttavia, queste librerie vengono in genere implementate nel linguaggio di programmazione stesso (ad esempio, i modelli di dominio C/C++ validi sono implementati in C/C++). L'integrazione di una libreria C/C++ in un editor scritto in TypeScript è tecnicamente possibile, ma difficile da eseguire.

### <a name="language-servers"></a>Server di linguaggio

Un altro approccio consiste nell'eseguire la libreria nel proprio processo e usare la comunicazione tra processi per comunicare con esso. I messaggi inviati in avanti e indietro formano un protocollo. Il protocollo LSP (Language Server Protocol) è il prodotto di standardizzazione dei messaggi scambiati tra uno strumento di sviluppo e un processo server di linguaggio. L'uso di server di lingue o demoni non è un concetto nuovo o innovativo. Gli editor come vim e Emacs lo fanno per un po' di tempo per fornire supporto semantico per il completamento automatico. Lo scopo dello LSP è quello di semplificare questi tipi di integrazioni e fornire un Framework utile per esporre le funzionalità del linguaggio a un'ampia gamma di strumenti.

La presenza di un protocollo comune consente l'integrazione delle funzionalità del linguaggio di programmazione in uno strumento di sviluppo con un minimo sforzo riutilizzando un'implementazione esistente del modello di dominio del linguaggio. Un server di linguaggio back-end può essere scritto in PHP, Python o Java e il LSP consente di integrarlo facilmente in un'ampia gamma di strumenti. Il protocollo funziona a un livello di astrazione comune, in modo che uno strumento possa offrire servizi di linguaggio avanzati senza la necessità di comprendere completamente le sfumature specifiche del modello di dominio sottostante.

## <a name="how-work-on-the-lsp-started"></a>Come iniziare a usare LSP

Lo LSP si è evoluto nel tempo e attualmente è alla versione 3,0. È stata avviata quando il concetto di server di linguaggio è stato prelevato da OmniSharp per fornire funzionalità di modifica avanzate per C#. Inizialmente, OmniSharp usava il protocollo HTTP con un payload JSON ed è stato integrato in diversi editor, tra cui [Visual Studio Code](https://code.visualstudio.com).

Intorno allo stesso tempo, Microsoft ha iniziato a lavorare su un server di linguaggio TypeScript, con l'idea di supportare TypeScript in Editor come Emacs e il testo sublime. In questa implementazione, un editor comunica tramite stdin/stdout con il processo del server TypeScript e usa un payload JSON ispirato dal protocollo del debugger V8 per le richieste e le risposte. Il server TypeScript è stato integrato nel plug-in TypeScript sublime e VS Code per la modifica avanzata di TypeScript.

Dopo aver integrato due server di linguaggi diversi, il team di VS Code ha iniziato a esplorare un protocollo Common Language Server per gli editor e gli IDE. Un protocollo comune consente a un provider di linguaggio di creare un unico server di linguaggio che può essere utilizzato da IDE diversi. Un consumer del server di linguaggio deve solo implementare il lato client del protocollo una sola volta. Ciò comporta una situazione di vittoria per il provider del linguaggio e il consumer di lingua.

Il protocollo del server di linguaggio è stato avviato con il protocollo usato dal server TypeScript, che è stato ampliato con altre funzionalità di linguaggio ispirate all'API del linguaggio VS Code. Il protocollo è supportato da JSON-RPC per la chiamata remota, grazie alla semplicità e alle librerie esistenti.

Il team di VS Code ha creato un prototipo per il protocollo implementando diversi server del linguaggio di disinstallazione che rispondono alle richieste di lanugine (analisi) di un file e restituiscono un set di avvisi ed errori rilevati. L'obiettivo è quello di infilare un file quando l'utente modifica in un documento, il che significa che vi saranno molte richieste di residuo durante una sessione dell'editor. È stato opportuno tenere operativo un server in modo che non fosse necessario avviare un nuovo processo di creazione di pelucchi per ogni modifica dell'utente. Sono stati implementati diversi server di pelucchi, incluse le estensioni ESLint e TSLint di VS Code. Questi due server di pelucchi sono implementati in TypeScript/JavaScript ed eseguiti su Node.js. Condividono una libreria che implementa la parte client e server del protocollo.

## <a name="how-the-lsp-works"></a>Funzionamento dello LSP

Un server di linguaggio viene eseguito in un proprio processo e strumenti come Visual Studio o VS Code comunicano con il server usando il protocollo del linguaggio su JSON-RPC. Un altro vantaggio del server di linguaggio che opera in un processo dedicato è che si evitano problemi di prestazioni correlati a un singolo modello di processo. Il canale di trasporto effettivo può essere stdio, Sockets, Named Pipes o node IPC se il client e il server sono scritti in Node.js.

Di seguito è riportato un esempio di come uno strumento e un server di linguaggio comunicano durante una sessione di modifica di routine:

![diagramma di flusso di LSP](media/lsp-flow-diagram.png)

* **L'utente apre un file (noto come documento) nello strumento**: lo strumento notifica al server di lingua che un documento è aperto (' textDocument/didopen '). Da questo momento in poi, la verità sul contenuto del documento non si trova più nel file system ma è mantenuta dallo strumento in memoria.

* **L'utente esegue modifiche**: lo strumento notifica al server la modifica del documento (' TextDocument/didChange ') e le informazioni semantiche del programma vengono aggiornate dal server di linguaggio. A questo punto, il server di linguaggio analizza queste informazioni e notifica allo strumento gli errori e gli avvisi rilevati (' textDocument/publishDiagnostics ').

* **L'utente esegue "Vai a definizione" su un simbolo nell'editor**: lo strumento invia una richiesta ' textDocument/Definition ' con due parametri: (1) l'URI del documento e (2) la posizione del testo dalla quale è stata avviata la richiesta Vai a definizione per il server. Il server risponde con l'URI del documento e la posizione della definizione del simbolo all'interno del documento.

* **L'utente chiude il documento (file)**: una notifica di tipo ' TextDocument/didClose ' viene inviata dallo strumento, indicando al server di linguaggio che il documento non è più in memoria e che il contenuto corrente è aggiornato nel file System.

In questo esempio viene illustrato il modo in cui il protocollo comunica con il server di linguaggio a livello di funzionalità dell'editor quali "Vai a definizione", "Trova tutti i riferimenti". I tipi di dati usati dal protocollo sono l'editor o i tipi di dati dell'IDE, ad esempio il documento di testo attualmente aperto e la posizione del cursore. I tipi di dati non sono al livello di un modello di dominio del linguaggio di programmazione che in genere fornisce alberi della sintassi astratta e simboli del compilatore, ad esempio tipi risolti, spazi dei nomi,.... Il protocollo viene semplificato in modo significativo.

Esaminiamo ora la richiesta ' textDocument/Definition ' in modo più dettagliato. Di seguito sono riportati i payload che passano tra lo strumento client e il server di linguaggio per la richiesta "Vai a definizione" in un documento C++.

Questa è la richiesta:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Risposta:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

In Retrospect, la descrizione dei tipi di dati a livello dell'editor anziché al livello del modello di linguaggio di programmazione è uno dei motivi del successo del protocollo server di linguaggio. È molto più semplice standardizzare un URI del documento di testo o una posizione del cursore rispetto alla standardizzazione di un albero della sintassi astratta e dei simboli del compilatore in diversi linguaggi di programmazione.

Quando un utente utilizza linguaggi diversi, VS Code in genere avvia un server di linguaggio per ogni linguaggio di programmazione. Nell'esempio seguente viene illustrata una sessione in cui l'utente lavora sui file Java e SASS.

![Java e Sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Capabilities

Non tutti i server di linguaggio sono in grado di supportare tutte le funzionalità definite dal protocollo. Pertanto, il client e il server annunciano la funzionalità supportata impostata tramite "funzionalità". Ad esempio, un server annuncia che è in grado di gestire la richiesta ' textDocument/Definition ', ma potrebbe non gestire la richiesta ' Workspace/symbol '. Analogamente, i client possono annunciare che sono in grado di fornire le notifiche di "informazioni sul salvataggio" prima del salvataggio di un documento, in modo che un server possa calcolare le modifiche testuali per formattare automaticamente il documento modificato.

## <a name="integrating-a-language-server"></a>Integrazione di un server di linguaggio

L'integrazione effettiva di un server di linguaggio in un particolare strumento non è definita dal protocollo server del linguaggio e viene lasciata agli implementatori degli strumenti. Alcuni strumenti integrano i server di linguaggio in modo generico mediante un'estensione che può avviare e comunicare con qualsiasi tipo di server di linguaggio. Altri, ad esempio VS Code, creano un'estensione personalizzata per ogni server di linguaggio, in modo che un'estensione sia ancora in grado di fornire alcune funzionalità del linguaggio personalizzate.

Per semplificare l'implementazione dei client e dei server di linguaggio, sono disponibili librerie o SDK per le parti client e server. Queste librerie vengono fornite per diverse lingue. È ad esempio disponibile un [modulo NPM client di linguaggio](https://www.npmjs.com/package/vscode-languageclient) per semplificare l'integrazione di un server di linguaggio in un'estensione vs code e un altro [modulo NPM del server](https://www.npmjs.com/package/vscode-languageserver) di linguaggio per scrivere un server di linguaggio utilizzando Node.js. Questo è l' [elenco](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) corrente delle librerie di supporto.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Uso del protocollo server di linguaggio in Visual Studio

* [Aggiunta di un'estensione del protocollo server di linguaggio](adding-an-lsp-extension.md) : informazioni sull'integrazione di un server di linguaggio in Visual Studio.
