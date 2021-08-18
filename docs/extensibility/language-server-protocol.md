---
title: Panoramica del protocollo del server di linguaggio | Microsoft Docs
description: Informazioni sul modo in cui il protocollo del server di linguaggio fornisce un framework utile per esporre le funzionalità del linguaggio a un'ampia gamma di strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 652164ec8553f0a332130d01f9c9d3a6d0537224
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152315"
---
# <a name="language-server-protocol"></a>Protocollo di server di linguaggio

## <a name="what-is-the-language-server-protocol"></a>Che cos'è il protocollo del server di linguaggio?

Il supporto di funzionalità di modifica avanzate come i completamenti automatici del codice sorgente o **Vai** a definizione per un linguaggio di programmazione in un editor o ide è tradizionalmente molto complesso e dispendioso in termini di tempo. In genere richiede la scrittura di un modello di dominio (uno scanner, un parser, un controllo dei tipi, un generatore e altro ancora) nel linguaggio di programmazione dell'editor o dell'IDE. Ad esempio, il plug-in Eclipse CDT, che fornisce il supporto per C/C++ nell'IDE di Eclipse, è scritto in Java perché l'IDE di Eclipse stesso è scritto in Java. Seguendo questo approccio, si intende l'implementazione di un modello di dominio C/C++ in TypeScript per Visual Studio Code e di un modello di dominio separato in C# per Visual Studio.

La creazione di modelli di dominio specifici del linguaggio è anche molto più semplice se uno strumento di sviluppo può riutilizzare le librerie specifiche del linguaggio esistenti. Tuttavia, queste librerie vengono in genere implementate nel linguaggio di programmazione stesso (ad esempio, i modelli di dominio C/C++ sono implementati in C/C++). L'integrazione di una libreria C/C++ in un editor scritto in TypeScript è tecnicamente possibile ma difficile da eseguire.

### <a name="language-servers"></a>Server di linguaggio

Un altro approccio consiste nell'eseguire la libreria nel proprio processo e usare la comunicazione tra processi per comunicare con essa. I messaggi inviati avanti e indietro formano un protocollo. Il protocollo LSP (Language Server Protocol) è il prodotto della standardizzazione dei messaggi s scambiati tra uno strumento di sviluppo e un processo del server di linguaggio. L'uso di server di linguaggi o di lingue non è un'idea nuova o nuova. Editor come Vim ed Emacs hanno fatto questo da tempo per fornire il supporto per il completamento automatico semantico. L'obiettivo di LSP era semplificare questi tipi di integrazioni e fornire un framework utile per esporre le funzionalità del linguaggio a un'ampia gamma di strumenti.

La presenza di un protocollo comune consente l'integrazione delle funzionalità del linguaggio di programmazione in uno strumento di sviluppo con problemi minimi riutilizzando un'implementazione esistente del modello di dominio del linguaggio. Un back-end del server di linguaggio può essere scritto in PHP, Python o Java e LSP consente di integrarlo facilmente in un'ampia gamma di strumenti. Il protocollo funziona a un livello comune di astrazione in modo che uno strumento possa offrire servizi di linguaggio completi senza dover comprendere appieno le sfumature specifiche del modello di dominio sottostante.

## <a name="how-work-on-the-lsp-started"></a>Come è stato avviato il servizio LSP

L'LSP si è evoluto nel tempo e oggi è alla versione 3.0. È iniziato quando OmniSharp ha scelto il concetto di server di linguaggio per offrire funzionalità di modifica avanzate per C#. OmniSharp ha inizialmente usato il protocollo HTTP con un payload JSON ed è stato integrato in diversi editor, tra [cui Visual Studio Code](https://code.visualstudio.com).

Nello stesso periodo Microsoft ha iniziato a lavorare su un server di linguaggio TypeScript, con l'idea di supportare TypeScript in editor come Emacs e Sublime Text. In questa implementazione, un editor comunica tramite stdin/stdout con il processo del server TypeScript e usa un payload JSON ispirata al protocollo del debugger V8 per le richieste e le risposte. Il server TypeScript è stato integrato nel plug-in TypeScript Sublime e VS Code la modifica di TypeScript.

Dopo aver integrato due server di linguaggi diversi, il team VS Code ha iniziato a esplorare un protocollo server di linguaggio comune per editor e IDE. Un protocollo comune consente a un provider di linguaggio di creare un singolo server di linguaggio che può essere utilizzato da diversi ID. Un consumer del server di linguaggio deve implementare il lato client del protocollo una sola volta. Ciò comporta una situazione win-win sia per il provider di linguaggio che per il consumer del linguaggio.

Il protocollo del server di linguaggio è stato avviato con il protocollo usato dal server TypeScript, espandendo il protocollo con altre funzionalità del linguaggio iscritte all'API VS Code linguaggio. Il protocollo è supportato con JSON-RPC per la chiamata remota a causa della semplicità e delle librerie esistenti.

Il team VS Code ha prototipato il protocollo implementando diversi server di linguaggio linter che rispondono alle richieste di lint (analisi) di un file e restituiscono un set di avvisi ed errori rilevati. L'obiettivo era lint di un file quando l'utente modifica in un documento, il che significa che saranno presenti molte richieste di lint durante una sessione dell'editor. È stato opportuno mantenere un server operativo in modo che non fosse necessario eseguire un nuovo processo di linting per ogni modifica dell'utente. Sono stati implementati diversi server linter, VS Code estensioni ESLint e TSLint di VS Code. Questi due server linter vengono entrambi implementati in TypeScript/JavaScript ed eseguiti in Node.js. Condividono una libreria che implementa la parte client e server del protocollo.

## <a name="how-the-lsp-works"></a>Funzionamento di LSP

Un server di linguaggio viene eseguito nel proprio processo e strumenti come Visual Studio o VS Code comunicano con il server usando il protocollo del linguaggio su JSON-RPC. Un altro vantaggio del server di linguaggio che opera in un processo dedicato è che vengono evitati i problemi di prestazioni correlati a un singolo modello di processo. Il canale di trasporto effettivo può essere stdio, socket, named pipe o node ipc se sia il client che il server sono scritti in Node.js.

Di seguito è riportato un esempio di come uno strumento e un server di linguaggio comunicano durante una sessione di modifica di routine:

![Diagramma di flusso lsp](media/lsp-flow-diagram.png)

* **L'utente apre un file (detto documento)** nello strumento : lo strumento notifica al server di lingua che un documento è aperto ('textDocument/didOpen'). Da questo momento in poi, la verità sul contenuto del documento non è più sul file system ma viene mantenuta dallo strumento in memoria.

* **L'utente** apporta modifiche: lo strumento notifica al server la modifica del documento ('textDocument/didChange') e le informazioni semantiche del programma vengono aggiornate dal server del linguaggio. In questo caso, il server di linguaggio analizza queste informazioni e invia una notifica all'utilità con gli errori e gli avvisi rilevati ('textDocument/publishDiagnostics').

* L'utente esegue **"Vai a definizione"** su un simbolo nell'editor: lo strumento invia una richiesta 'textDocument/definition' con due parametri: (1) l'URI del documento e (2) la posizione del testo da cui è stata avviata la richiesta Vai a definizione al server. Il server risponde con l'URI del documento e la posizione della definizione del simbolo all'interno del documento.

* L'utente chiude il documento **(file):** viene inviata una notifica 'textDocument/didClose' dallo strumento, che informa il server di lingua che il documento non è più in memoria e che il contenuto corrente è ora aggiornato nel file system.

Questo esempio illustra come il protocollo comunica con il server di linguaggio a livello di funzionalità dell'editor, ad esempio "Vai a definizione", "Trova tutti i riferimenti". I tipi di dati usati dal protocollo sono "tipi di dati" dell'editor o dell'IDE, ad esempio il documento di testo attualmente aperto e la posizione del cursore. I tipi di dati non sono al livello di un modello di dominio del linguaggio di programmazione che in genere fornisce alberi della sintassi astratti e simboli del compilatore (ad esempio, tipi risolti, spazi dei nomi, ...). In questo modo il protocollo viene semplificato in modo significativo.

Si esamini ora la richiesta "textDocument/definition" in modo più dettagliato. Di seguito sono riportati i payload che passano tra lo strumento client e il server di linguaggio per la richiesta "Vai a definizione" in un documento C++.

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

In analisi retrospettiva, la descrizione dei tipi di dati a livello dell'editor anziché a livello del modello del linguaggio di programmazione è uno dei motivi per il successo del protocollo del server di linguaggio. È molto più semplice standardizzare un URI del documento di testo o una posizione del cursore rispetto alla standardizzazione di un albero della sintassi astratta e dei simboli del compilatore in linguaggi di programmazione diversi.

Quando un utente utilizza linguaggi diversi, VS Code in genere avvia un server di linguaggio per ogni linguaggio di programmazione. L'esempio seguente illustra una sessione in cui l'utente lavora su file Java e SASS.

![java e sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funzionalità

Non tutti i server di linguaggio possono supportare tutte le funzionalità definite dal protocollo. Pertanto, il client e il server annunciano il set di funzionalità supportato tramite "funzionalità". Ad esempio, un server annuncia che può gestire la richiesta 'textDocument/definition', ma potrebbe non gestire la richiesta 'workspace/symbol'. Analogamente, i client possono annunciare di essere in grado di inviare notifiche sul salvataggio prima del salvataggio di un documento, in modo che un server possa calcolare modifiche testuali per formattare automaticamente il documento modificato.

## <a name="integrating-a-language-server"></a>Integrazione di un server di linguaggio

L'integrazione effettiva di un server di linguaggio in uno strumento specifico non è definita dal protocollo del server di linguaggio e viene lasciata agli implementatori dello strumento. Alcuni strumenti integrano i server di linguaggio in modo generico grazie a un'estensione in grado di avviare e parlare con qualsiasi tipo di server di linguaggio. Altri, ad esempio VS Code, creano un'estensione personalizzata per ogni server di linguaggio, in modo che un'estensione sia ancora in grado di fornire alcune funzionalità del linguaggio personalizzate.

Per semplificare l'implementazione di client e server di linguaggio, sono disponibili librerie o SDK per le parti client e server. Queste librerie vengono fornite per linguaggi diversi. Ad esempio, è disponibile un modulo [npm del client](https://www.npmjs.com/package/vscode-languageclient) di linguaggio per semplificare l'integrazione di un server di linguaggio in un'estensione VS Code e un altro modulo [npm](https://www.npmjs.com/package/vscode-languageserver) del server di linguaggio per scrivere un server di linguaggio usando Node.js. Questo è l'elenco [corrente delle](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) librerie di supporto.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Uso del protocollo del server di linguaggio in Visual Studio

* [Aggiunta di un'estensione del protocollo del server di](adding-an-lsp-extension.md) linguaggio: informazioni sull'integrazione di un server di linguaggio Visual Studio.
