---
title: Panoramica del protocollo Server Language | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a41bccbec31f11a30d5e9ccf0e97806d3e7efb4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023457"
---
# <a name="language-server-protocol"></a>Protocollo di server di linguaggio

## <a name="what-is-the-language-server-protocol"></a>Che cos'è il protocollo di Server di linguaggio?

Supporti ricche funzionalità di modifica, ad esempio auto-completamento del codice sorgente oppure **Vai a definizione** per un linguaggio di programmazione in un editor o l'IDE è in genere molto complessa e richiedere molto tempo. In genere richiede la scrittura di un modello di dominio (uno scanner, parser, uno strumento di controllo di tipo, un generatore e altro ancora) nel linguaggio di programmazione dell'editor o IDE. Ad esempio, il plug-in Eclipse GDTTO, che fornisce il supporto per C/C++ nell'IDE di Eclipse è scritto in Java, poiché l'IDE di Eclipse è scritto in Java. Seguendo questo approccio, comporterebbe l'implementazione di un modello di dominio in TypeScript per Visual Studio Code C/C++ e un modello di dominio distinti in c# per Visual Studio.

Creazione di modelli di dominio specifico del linguaggio sono anche molto più semplice se uno strumento di sviluppo può riutilizzare librerie specifiche della lingua esistenti. Tuttavia, queste librerie sono in genere implementate nel linguaggio di programmazione stesso (ad esempio, buona C/C++ dominio modelli vengono implementati in C/C++). L'integrazione di una libreria di C/C++ in un editor scritto in TypeScript è tecnicamente possibile ma difficili da eseguire.

### <a name="language-servers"></a>Server di linguaggio

Un altro approccio consiste nell'eseguire la libreria nel proprio processo e usano la comunicazione interprocesso per comunicare con ad esso. I messaggi inviati e restituiti costituiscono un protocollo. Il protocollo di server di linguaggio (LSP) è il prodotto di standardizzare i messaggi scambiati tra uno strumento di sviluppo e un processo del server di linguaggio. Uso della lingua server o demons non è un concetto nuovo o novel. Editor, ad esempio Vim ed Emacs gestiscono questo per un certo tempo fornire il supporto di semantica di completamento automatico. L'obiettivo del rappresentante LSP memorizzato era semplificare questi tipi di integrazioni e forniscono un framework utile per l'esposizione di funzionalità del linguaggio per un'ampia gamma di strumenti.

La disponibilità di un protocollo comune consente l'integrazione di funzionalità del linguaggio di programmazione in uno strumento di sviluppo con la massima semplicità grazie al riutilizzo un'implementazione esistente del modello di dominio del linguaggio. Un server di linguaggio back-end può essere scritta in PHP, Python o Java e il rappresentante LSP memorizzato permette di essere facilmente integrati in un'ampia gamma di strumenti. Il protocollo lavora a un livello di astrazione comune in modo che uno strumento può offrire servizi di linguaggio avanzato senza la necessità di conoscere a fondo le varie sfumature specifiche per il modello di dominio sottostante.

## <a name="how-work-on-the-lsp-started"></a>Come funzionano nel rappresentante LSP memorizzato avviato

Il rappresentante LSP memorizzato si è evoluto nel corso del tempo e attualmente si trova alla versione 3.0. Viene avviato quando il concetto di un server di linguaggio è stato prelevato omnisharp per fornire avanzate funzionalità di modifica per c#. Inizialmente, OmniSharp utilizzato il protocollo HTTP con un payload JSON ed è stato integrato in diversi editor tra cui [Visual Studio Code](https://code.visualstudio.com).

Intorno alla stessa ora, Microsoft è iniziato a lavorare in un server di linguaggio TypeScript, con l'idea di supporto di TypeScript negli editor come Emacs e Sublime Text. In questa implementazione, un editor comunica tramite stdin/stdout con il processo server TypeScript e Usa un payload JSON ispirazione dal protocollo del debugger V8 per le richieste e risposte. Il server di TypeScript è stato integrato nel plug-in TypeScript Sublime e Visual Studio Code per la modifica di TypeScript avanzata.

Dopo avere integrato due server in lingue diverse, il team di Visual Studio Code è iniziato a esplorare un protocollo di server di linguaggio comune per gli editor e IDE. Un protocollo comune consente a un provider del linguaggio creare un server unico linguaggio che può essere utilizzato da diversi ambienti di sviluppo integrato. Un consumer di server di linguaggio deve solo implementare una sola volta il lato client del protocollo. Ciò comporta una situazione vincenti per il provider del linguaggio e il consumer di linguaggio.

Il protocollo di server di linguaggio avviato con il protocollo usato dal server di TypeScript, espanderlo con altre funzionalità del linguaggio traendo ispirazione dall'API del linguaggio di Visual Studio Code. Il protocollo è supportato con la RPC JSON per la chiamata remota a causa di sua semplicità e le librerie esistenti.

Visual Studio un file di codice con prototipo team il protocollo tramite l'implementazione di più server di linguaggio linter che risponde alle richieste di lint (analisi) e restituisce un set di errori e avvisi rilevati. L'obiettivo era di lint è un file come le modifiche dell'utente in un documento, il che significa che sarà presente un numero di richieste di Lint durante una sessione dell'editor. È parso logico per mantenere un server di backup e in esecuzione in modo che un nuovo processo di Lint non sono necessarie essere avviato per la modifica ogni utente. Sono stati implementati numerosi server linter, tra cui Visual Studio Code ESLint e TSLint estensioni. Questi due server linter vengono entrambi implementati in TypeScript/JavaScript ed eseguiti su Node. js. Queste versioni condividono una libreria che implementa la parte di client e server del protocollo.

## <a name="how-the-lsp-works"></a>Come funziona il rappresentante LSP memorizzato

Un server di linguaggio viene eseguito nel proprio processo e gli strumenti come Visual Studio o Vscode comunicano con il server utilizzando il protocollo di linguaggio la RPC JSON. Un altro vantaggio di operativo in un processo dedicato del server di linguaggio è evitare che problemi di prestazioni relativi a un modello singolo processo. Il canale del trasporto effettivo può essere stdio, socket, le named pipe o nodo ipc se il client e server vengono scritti in Node. js.

Di seguito è riportato un esempio per la modalità di comunicazione durante una routine di uno strumento e un server di linguaggio sessione di modifica:

![diagramma di flusso di Layered Service Provider](media/lsp-flow-diagram.png)

* **L'utente apre un file (definito come un documento) nello strumento**: Lo strumento di notifica al server di linguaggio che viene aperto un documento (' textDocument/didOpen'). D'ora in poi la verità in merito il contenuto del documento non è più nel file system ma mantenga lo strumento in memoria.

* **L'utente effettua modifiche**: Lo strumento di notifica al server sulla modifica del documento (' textDocument/didChange') e le informazioni semantiche del programma viene aggiornate dal server di linguaggio. Come in questo caso, il server di linguaggio analizza queste informazioni e invia una notifica lo strumento con gli errori e gli avvisi (' textDocument/publishDiagnostics').

* **L'utente esegue "Vai a definizione" su un simbolo nell'editor**: Lo strumento invia una richiesta di ' textDocument/definizione' con due parametri: (1) l'URI del documento e (2) la posizione del testo da dove Vai a nella richiesta della definizione è stato avviato nel server. Il server risponde con l'URI del documento e la posizione della definizione del simbolo all'interno del documento.

* **L'utente chiude il documento (file)**: Viene inviata una notifica di ' textDocument/didClose' dallo strumento, per informare il server di linguaggio che il documento è ora non è più in memoria e che il contenuto corrente è ora aggiornata nel file system.

Questo esempio viene illustrato come il protocollo comunica con il server di linguaggio al livello di funzionalità dell'editor, ad esempio "Vai a definizione", "Trova tutti i riferimenti". I tipi di dati utilizzati dal protocollo sono editor o ambiente IDE "tipi di dati", ad esempio il documento di testo aperto e la posizione del cursore. I tipi di dati non sono a livello di un linguaggio dominio del modello di programmazione che in genere fornisce gli alberi della sintassi astratta e simboli di compilazione (ad esempio, risolvere i tipi, spazi dei nomi,...). Questo semplifica notevolmente il protocollo.

Ora esaminiamo la richiesta ' textDocument/definizione' in modo più dettagliato. Di seguito sono i payload che passare tra lo strumento client e il server di linguaggio per la richiesta "Vai a definizione" in un documento di C++.

Si tratta della richiesta:

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

A posteriori, che descrive i tipi di dati a livello di editor anziché a livello del linguaggio del modello di programmazione è uno dei motivi per il successo del protocollo del server di linguaggio. È molto più semplice standardizzare un URI del documento di testo o una posizione del cursore confrontato con la standardizzazione dei simboli di struttura ad albero e del compilatore una sintassi astratta tra diversi linguaggi di programmazione.

Quando un utente sta usando diversi linguaggi, Visual Studio Code inizia in genere un server di linguaggio per ogni linguaggio di programmazione. L'esempio seguente viene illustrata una sessione in cui lavora l'utente nei file Java e il SASS.

![Java e il sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funzionalità

Non tutti i server di linguaggio può supportare tutte le funzionalità definite dal protocollo. Pertanto, il client e server annuncia i set di funzionalità supportate tramite 'capabilities'. Ad esempio, un server di notifica che è possibile gestire la richiesta ' textDocument/definizione', ma che non può gestire la richiesta di 'area di lavoro/symbol'. Analogamente, i client possono annunciare che sono in grado di fornire ' per salvare' notifiche prima di salvata un documento, in modo che un server può calcolare modifiche testuale per formattare automaticamente il documento modificato.

## <a name="integrating-a-language-server"></a>L'integrazione di un server di linguaggio

L'integrazione effettiva di un server di linguaggio in un determinato strumento non è definito dal protocollo del server di linguaggio e da sinistra a implementatori di strumento. Alcuni strumenti di integrano i server di linguaggio in modo generico facendo in modo che un'estensione che possa avviare e comunicare con qualsiasi tipo di server di linguaggio. Altri, ad esempio Visual Studio Code, creare un'estensione personalizzata per ogni server di linguaggio, in modo che un'estensione è comunque in grado di fornire alcune funzionalità del linguaggio personalizzato.

Per semplificare l'implementazione di client e server di linguaggio, sono disponibili librerie o gli SDK per le parti client e server. Queste librerie sono disponibili per diverse lingue. Ad esempio, è presente una [il modulo npm client di linguaggio](https://www.npmjs.com/package/vscode-languageclient) per facilitare l'integrazione di un server di linguaggio in un'estensione di Visual Studio Code e l'altra [modulo npm di lingua server](https://www.npmjs.com/package/vscode-languageserver) per scrivere un server di linguaggio con Node. js. Questo è l'oggetto corrente [elenco](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) delle librerie di supporto.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Tramite il protocollo di Server di linguaggio in Visual Studio

* [Aggiunta di un'estensione per il protocollo di Server di linguaggio](adding-an-lsp-extension.md) -informazioni sull'integrazione di un server di linguaggio in Visual Studio.
