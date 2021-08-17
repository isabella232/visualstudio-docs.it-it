---
title: Comandi devinit
description: Informazioni dettagliate su come usare i comandi devinit per installare i componenti.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e93e9c84b4f9448f212d7c55146a1e2eddc584e201c47e35d8388b3421f592ff
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390748"
---
# <a name="devinit-commands"></a>comandi devinit

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

## <a name="init"></a>Init

```console
devinit init
```

Inizializzare l'ambiente eseguendo gli strumenti specificati in un.devinit.js[ su](devinit-json.md) file.

### <a name="options-for-init"></a>Opzioni per init

Opzioni facoltative per il `devinit init` comando .

| Argomento             | Obbligatoria | Descrizione                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--file            | No       | Percorso del `.devinit.json` file.                                         |
| --error-action       | No       | Specifica come gestire gli errori. Opzioni: Arresta, Ignora, Continua (impostazione predefinita).|
| -v,--verbose         | No       | Generare un output dettagliato.                                                      |
| -n,--dry-run         | No       | Esecuzione a secco.                                                                  |

#### <a name="--file-argument"></a>Argomento --file

Specifica il percorso _dell'devinit.jsnel_ file. Se --file non viene specificato, viene cercato un file predefinito nei percorsi seguenti:

* {current-directory} \\.devinit.jssu
* {current-directory} \\devinit.jssu
* {current-directory} \\ . devinit \\.devinit.jssu
* {current-directory} \\ . devinit \\devinit.jssu
* {current-directory} \\ devinit \\.devinit.jssu
* {current-directory} \\ devinit \\devinit.jssu
* {current-directory} \\ . devcontainer \\.devinit.jssu
* {current-directory} \\ . devcontainer \\devinit.jssu

> [!NOTE]
> Se vengono trovati più file predefiniti, devinit userà il file visualizzato per primo nell'elenco precedente.

#### <a name="--error-action-argument"></a>Argomento --error-action

Vedere [di seguito](#options-for-run).

#### <a name="--verbose-switch"></a>Opzione --verbose

Vedere [di seguito](#options-for-run).

#### <a name="--dry-run-switch"></a>Opzione --dry-run

Vedere [di seguito](#options-for-run).

## <a name="run"></a>Esegui

```console
devinit run -t <toolname>
```

Esegue lo strumento specifico. I parametri sono elencati di seguito. Per [un utilizzo](devinit-tool-list.md) specifico, vedere la documentazione relativa a ogni strumento.

### <a name="options-for-run"></a>Opzioni per l'esecuzione

Opzioni per il `devinit run` comando .

| Argomento                                      | Obbligatoria | Descrizione                                                                          |
|-----------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--tool                                     | Sì      | Obbligatorio. Nome dello strumento.                                                             |
| -i,--input                                    | No       | Valore di input dello strumento. Ad esempio, un nome file, un pacchetto o un nome.                     |
| --error-action                                | No       | Specifica come gestire gli errori dello strumento: Arresta, Ignora, Continua. L'impostazione predefinita è l'arresto. |
| -v,--verbose                                  | No       | Generare un output dettagliato.                                                                 |
| -n,--dry-run                                  | No       | Esecuzione a secco.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; ... &lt; argN&gt;  | No       | Argomenti aggiuntivi della riga di comando per lo strumento.                                       |

#### <a name="--error-action-argument"></a>Argomento --error-action

Specifica l'azione da eseguire se uno strumento restituisce un codice di uscita diverso da zero. I valori validi sono:

| Argomento | Descrizione                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Continuare a elaborare altri strumenti dopo aver generato un errore in un errore standard. Il devinit.exe di uscita è diverso da zero (errore). Questo comportamento è simile all'azione Arresta errore, ma l'elaborazione continua. `continue` è l'azione di errore predefinita per il comando init.              |
| ignore   | Continuare a elaborare altri strumenti dopo aver generato un avviso nell'output standard. Il codice di uscita del processo DevInit deve essere sempre zero (operazione riuscita). `ignore`L'impostazione ignora tutti gli errori.                                                                                                      |
| stop     | Genera un errore per gli errori standard e arresta gli strumenti di elaborazione. Il devinit.exe di uscita è diverso da zero (errore). Questa operazione è simile all'azione continue error, ma l'elaborazione viene interrotta al primo errore rilevato. `stop` è l'azione di errore predefinita per tutti i comandi ad eccezione di init. |

#### <a name="--dry-run-switch"></a>Opzione --dry-run

Comandi dello strumento Echo che verranno eseguiti. Alcuni strumenti possono intraprendere altre azioni, come documentato per tale strumento. 

#### <a name="--verbose-switch"></a>Opzione --verbose

Generare output dettagliato nell'output standard. Se lo strumento da eseguire supporta un'opzione dettagliata, propagare l'opzione dettagliata per lo strumento.

#### <a name="--dry-run-switch"></a>Opzione --dry-run

Comandi dello strumento Echo che vengono eseguiti, ma non eseguono strumenti.

#### <a name="additional-command-line-arguments"></a>Argomenti aggiuntivi della riga di comando

`<arg>`L'uso di un oggetto che include uno spazio nel relativo valore deve includere una coppia aggiuntiva di virgolette precedute da un carattere di escape.

```console
devinit run -t <toolname> -<somearg> "<some value>"
```

Per installare dotnet in una directory `C:\Program Files\dotnet` specifica:

```console
devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>Elenco

```console
devinit list
```

Stampa un elenco di tutti gli strumenti disponibili.

## <a name="show"></a>Mostra

```console
devinit show -t <toolname>
```

| Argomento       | Obbligatoria | Descrizione                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--tool      | Sì      | Obbligatorio. Nome dello strumento.                                                             |

Stampa le informazioni della Guida per un determinato strumento.

## <a name="version"></a>Versione

```console
devinit version
```

Stampa le informazioni sulla versione corrente per devinit.

## <a name="help"></a>Help

```console
devinit help
devinit help list
```

Stampa il testo della Guida per devinit o per un comando `devinit <command>` specifico.
 
