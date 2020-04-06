---
title: Cenni preliminari sul protocollo di Language Server - Documenti Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703111"
---
# <a name="language-server-protocol"></a>Protocollo di server di linguaggio

## <a name="what-is-the-language-server-protocol"></a>Che cos'è il protocollo Language Server?

Il supporto di funzionalità di modifica avanzate come i completamenti automatici del codice sorgente o **Vai a definizione** per un linguaggio di programmazione in un editor o IDE è tradizionalmente molto impegnativo e richiede molto tempo. In genere richiede la scrittura di un modello di dominio (uno scanner, un parser, un controllo dei tipi, un generatore e altro ancora) nel linguaggio di programmazione dell'editor o IDE. Ad esempio, il plug-in Eclipse CDT, che fornisce il supporto per C/Cè nell'IDE Eclipse è scritto in Java poiché l'IDE Eclipse stesso è scritto in Java. Seguendo questo approccio, si intende l'implementazione di un modello di dominio C/C , in TypeScript per Visual Studio Code, e un modello di dominio separato in C , per Visual Studio.

La creazione di modelli di dominio specifici del linguaggio è anche molto più semplice se uno strumento di sviluppo può riutilizzare librerie specifiche del linguaggio esistenti. Tuttavia, queste librerie vengono in genere implementate nel linguaggio di programmazione stesso (ad esempio, i buoni modelli di dominio C/C, sono implementati in C/C. L'integrazione di una libreria C/C è in un editor scritto in TypeScript è tecnicamente possibile ma difficile da fare.

### <a name="language-servers"></a>Server di lingua

Un altro approccio consiste nell'eseguire la libreria nel proprio processo e utilizzare la comunicazione tra processi per comunicare con essa. I messaggi inviati avanti e indietro formano un protocollo. Il protocollo LSP (Language Server Protocol) è il prodotto della standardizzazione dei messaggi scambiati tra uno strumento di sviluppo e un processo del server di linguaggio. L'utilizzo di server di linguaggio o demoni non è un'idea nuova o nuova. Editor come Vim ed Emacs lo fanno da qualche tempo per fornire supporto per il completamento automatico semantico. L'obiettivo del provider LSP era semplificare questo tipo di integrazioni e fornire un framework utile per esporre le funzionalità del linguaggio a una varietà di strumenti.

La disponibilità di un protocollo comune consente l'integrazione delle funzionalità del linguaggio di programmazione in uno strumento di sviluppo con il minimo scadere riutilizzando un'implementazione esistente del modello di dominio del linguaggio. Un server back-end del linguaggio potrebbe essere scritto in PHP, Python o Java e l'LSP consente di integrarlo facilmente in una varietà di strumenti. Il protocollo funziona a un livello comune di astrazione in modo che uno strumento possa offrire servizi di linguaggio avanzati senza la necessità di comprendere appieno le sfumature specifiche del modello di dominio sottostante.

## <a name="how-work-on-the-lsp-started"></a>Come è iniziato il lavoro sull'LSP

L'LSP si è evoluto nel tempo e oggi è alla versione 3.0. È iniziato quando il concetto di server di linguaggio è stato scelto da OmniSharp per fornire funzionalità di modifica avanzate per C . Inizialmente, OmniSharp ha utilizzato il protocollo HTTP con un payload JSON ed è stato integrato in diversi editor, tra cui [Visual Studio Code](https://code.visualstudio.com).

Più o meno nello stesso periodo, Microsoft ha iniziato a lavorare su un server di linguaggio TypeScript, con l'idea di supportare TypeScript in editor come Emacs e Sublime Text. In questa implementazione, un editor comunica tramite stdin/stdout con il processo server TypeScript e usa un payload JSON ispirato al protocollo del debugger V8 per richieste e risposte. Il server TypeScript è stato integrato nel plug-in TypeScript Sublime e nel codice VS per la modifica avanzata di TypeScript.

Dopo aver integrato due server di linguaggio diversi, il team di codice VS ha iniziato a esplorare un protocollo di server di linguaggio comune per editor e IDE. Un protocollo comune consente a un provider di linguaggio di creare un singolo server di linguaggio che può essere utilizzato da diversi IDE. Un consumer di server di linguaggio deve implementare il lato client del protocollo una sola volta. Ciò si traduce in una situazione win-win sia per il provider di linguaggio che per il consumatore del linguaggio.

Il protocollo del server di linguaggio è iniziato con il protocollo utilizzato dal server TypeScript, espandendolo con più funzionalità del linguaggio ispirate all'API del linguaggio VS Code. Il protocollo è supportato con JSON-RPC per la chiamata remota grazie alla sua semplicità e alle librerie esistenti.

Il team del codice VS ha prototipo il protocollo implementando diversi server di linguaggio linter che rispondono alle richieste di un file lint (scan) e restituiscono un set di avvisi ed errori rilevati. L'obiettivo era quello di lint un file come l'utente modifica in un documento, il che significa che ci saranno molte richieste di linting durante una sessione di editor. Aveva senso mantenere un server in funzione in modo che non fosse necessario iniziare un nuovo processo di linting per ogni modifica dell'utente. Sono stati implementati diversi server linter, tra cui le estensioni ESLint e TSLint di VS Code. Questi due server linter sono entrambi implementati in TypeScript/JavaScript ed eseguiti su Node.js. Condividono una libreria che implementa la parte client e server del protocollo.

## <a name="how-the-lsp-works"></a>Come funziona l'LSP

Un server di linguaggio viene eseguito nel proprio processo e strumenti come Visual Studio o VS Code comunicano con il server utilizzando il protocollo del linguaggio su JSON-RPC. Un altro vantaggio del server di linguaggio che opera in un processo dedicato è che i problemi di prestazioni relativi a un singolo modello di processo vengono evitati. Il canale di trasporto effettivo può essere stdio, socket, named pipe o ipc del nodo se sia il client che il server sono scritti in Node.js.

Di seguito è riportato un esempio di come uno strumento e un server di linguaggio comunicano durante una sessione di modifica di routine:

![Diagramma di flusso dellsp](media/lsp-flow-diagram.png)

* **L'utente apre un file (denominato documento) nello strumento**: lo strumento notifica al server di linguaggio che un documento è aperto ('textDocument/didOpen'). D'ora in poi, la verità sul contenuto del documento non è più sul file system, ma mantenuta dallo strumento in memoria.

* **L'utente apporta modifiche**: Lo strumento notifica al server la modifica del documento ('textDocument/didChange') e le informazioni semantiche del programma vengono aggiornate dal server di linguaggio. In questo caso, il server di linguaggio analizza queste informazioni e notifica allo strumento gli errori e gli avvisi rilevati ('textDocument/publishDiagnostics').

* **L'utente esegue "Vai alla definizione" su un simbolo nell'editor**: lo strumento invia una richiesta 'textDocument/definition' con due parametri: (1) l'URI del documento e (2) la posizione del testo da cui è stata avviata la richiesta Vai a definizione al server. Il server risponde con l'URI del documento e la posizione della definizione del simbolo all'interno del documento.

* **L'utente chiude il documento (file):** una notifica 'textDocument/didClose' viene inviata dallo strumento, informando il server di linguaggio che il documento non è più in memoria e che il contenuto corrente è ora aggiornato sul file system.

In questo esempio viene illustrato come il protocollo comunica con il server di linguaggio a livello di funzionalità dell'editor, ad esempio "Vai a definizione", "Trova tutti i riferimenti". I tipi di dati utilizzati dal protocollo sono editor o IDE 'tipi di dati' come il documento di testo attualmente aperto e la posizione del cursore. I tipi di dati non sono a livello di un modello di dominio del linguaggio di programmazione che in genere fornisce alberi della sintassi astratti e simboli del compilatore (ad esempio, tipi risolti, spazi dei nomi, ...). Ciò semplifica notevolmente il protocollo.

Esaminiamo ora la richiesta 'textDocument/definition' in modo più dettagliato. Di seguito sono riportati i payload che vanno tra lo strumento client e il server di linguaggio per la richiesta "Vai a definizione" in un documento di C .

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

Questa è la risposta:

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

In retrospettiva, la descrizione dei tipi di dati a livello dell'editor piuttosto che a livello del modello del linguaggio di programmazione è uno dei motivi per il successo del protocollo del server di linguaggio. È molto più semplice standardizzare un URI di documento di testo o una posizione del cursore rispetto alla standardizzazione di un albero della sintassi astratto e di simboli del compilatore tra diversi linguaggi di programmazione.

Quando un utente lavora con linguaggi diversi, il codice VS in genere avvia un server di linguaggio per ogni linguaggio di programmazione. L'esempio seguente mostra una sessione in cui l'utente lavora sui file Java e SASS.

![java e sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Capabilities

Non tutti i server di linguaggio possono supportare tutte le funzionalità definite dal protocollo. Pertanto, il client e il server annuncia il set di funzionalità supportate tramite 'funzionalità'. Ad esempio, un server annuncia che può gestire la richiesta 'textDocument/definition', ma potrebbe non gestire la richiesta 'workspace/symbol'. Allo stesso modo, i client possono annunciare di essere in grado di fornire notifiche "in via di salvataggio" prima che un documento venga salvato, in modo che un server possa calcolare le modifiche testuali per formattare automaticamente il documento modificato.

## <a name="integrating-a-language-server"></a>Integrazione di un server di linguaggio

L'effettiva integrazione di un server di linguaggio in un particolare strumento non è definita dal protocollo del server di linguaggio e viene lasciata agli implementatori dello strumento. Alcuni strumenti integrano i server di linguaggio in modo generico con un'estensione che può avviare e parlare con qualsiasi tipo di server di linguaggio. Altri, come il codice VS, creare un'estensione personalizzata per ogni server di linguaggio, in modo che un'estensione è ancora in grado di fornire alcune funzionalità del linguaggio personalizzato.

Per semplificare l'implementazione di server e client di linguaggio, sono disponibili librerie o SDK per le parti client e server. Queste librerie sono fornite per lingue diverse. Ad esempio, è disponibile un [modulo di linguaggio client npm](https://www.npmjs.com/package/vscode-languageclient) per facilitare l'integrazione di un server di linguaggio in un'estensione di codice VS e un altro [modulo npm server di linguaggio](https://www.npmjs.com/package/vscode-languageserver) per scrivere un server di linguaggio utilizzando Node.js. Questo è [l'elenco](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) corrente delle librerie di supporto.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Utilizzo del protocollo del server di linguaggio in Visual StudioUsing the Language Server Protocol in Visual Studio

* [Aggiunta di un'estensione Language Server Protocol:](adding-an-lsp-extension.md) informazioni sull'integrazione di un server di linguaggio in Visual Studio.Adding a Language Server Protocol extension - Learn about integrating a language server into Visual Studio.
