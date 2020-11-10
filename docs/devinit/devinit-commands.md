---
title: Comandi devinit
description: Informazioni dettagliate su come usare i comandi devinit per installare i componenti.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 153864a293ca25fdcf30f23b96f686737411c965
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435786"
---
# <a name="devinit-commands"></a>comandi devinit

## <a name="init"></a>Init

```console
devinit init
```

Inizializzare l'ambiente eseguendo gli strumenti specificati in un [.devinit.jssu](devinit-json.md) file.

### <a name="options-for-init"></a>Opzioni per init

Opzioni facoltative per il `devinit init` comando.

| Argomento             | Obbligatoria | Descrizione                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--file            | No       | Percorso del `.devinit.json` file.                                         |
| --Error-Action       | No       | Specifica la modalità di gestione degli errori. Opzioni: arresta, ignora, continua (impostazione predefinita).|
| -v,--verbose         | No       | Genera output dettagliato.                                                      |
| -n,--esecuzione a secco         | No       | Esecuzione a secco.                                                                  |

#### <a name="--file-argument"></a>--argomento del file

Specifica il percorso del _devinit.jssul_ file. Se--file non è specificato, si cerca un file predefinito nei percorsi seguenti:

* {Current-directory} \\.devinit.js
* {Current-directory} \\devinit.js
* {Current-directory} \\ ..devinit.jsdi devinit \\
* {Current-directory} \\ .devinit.jsdi devinit \\
* {Current-directory} \\.devinit.jsdi devinit \\
* {Current-directory} \\devinit.jsdi devinit \\
* {Current-directory} \\ . devcontainer \\.devinit.json
* {Current-directory} \\ . devcontainer \\devinit.json

> [!NOTE]
> Se vengono trovati più file predefiniti, il file verrà usato per primo nell'elenco precedente.

#### <a name="--error-action-argument"></a>--Error-argomento azione

Vedere di [seguito](#options-for-run).

#### <a name="--verbose-switch"></a>opzione--verbose

Vedere di [seguito](#options-for-run).

#### <a name="--dry-run-switch"></a>--opzione di esecuzione a secco

Vedere di [seguito](#options-for-run).

## <a name="run"></a>Esegui

```console
devinit run -t <toolname>
```

Esegue lo strumento specifico. i parametri sono elencati di seguito. Vedere la [documentazione](devinit-tool-list.md) per ogni strumento per un utilizzo specifico.

### <a name="options-for-run"></a>Opzioni per l'esecuzione

Opzioni per il `devinit run` comando.

| Argomento                                      | Obbligatoria | Descrizione                                                                          |
|-----------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--strumento                                     | Sì      | Obbligatorio. Nome dello strumento.                                                             |
| -i,--input                                    | No       | Valore di input dello strumento. Ad esempio, un nome file, un pacchetto o un nome.                     |
| --Error-Action                                | No       | Specifica come gestire gli errori dello strumento: arresta, ignora, continua. Il valore predefinito è stop. |
| -v,--verbose                                  | No       | Genera output dettagliato.                                                                 |
| -n,--esecuzione a secco                                  | No       | Esecuzione a secco.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; ... &lt; argN&gt;  | No       | Argomenti aggiuntivi della riga di comando per lo strumento.                                       |

#### <a name="--error-action-argument"></a>--Error-argomento azione

Specifica l'azione da intraprendere se uno strumento restituisce un codice di uscita diverso da zero. I valori validi sono:

| Argomento | Descrizione                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Continua l'elaborazione di altri strumenti dopo l'emissione di un errore in errore standard. Il codice di uscita del devinit.exe è diverso da zero (esito negativo). Questo comportamento è simile all'azione arresta errore, ma l'elaborazione continua. `continue` è l'azione di errore predefinita per il comando init.              |
| ignore   | Continuare l'elaborazione di altri strumenti dopo l'emissione di un avviso nell'output standard. Il codice di uscita del processo devinilt deve essere sempre zero (esito positivo). L' `ignore` impostazione Ignora tutti gli errori.                                                                                                      |
| stop     | Genera un errore nell'errore standard e interrompe l'elaborazione degli strumenti. Il codice di uscita del devinit.exe è diverso da zero (esito negativo). È simile all'azione continua errore, ma l'elaborazione viene interrotta al primo errore rilevato. `stop` è l'azione di errore predefinita per tutti i comandi ad eccezione di init. |

#### <a name="--dry-run-switch"></a>--opzione di esecuzione a secco

Comandi echo Tool che verrebbero eseguiti. Alcuni strumenti potrebbero richiedere ulteriori azioni, come documentato per tale strumento. 

#### <a name="--verbose-switch"></a>opzione--verbose

Genera output dettagliato nell'output standard. Se lo strumento da eseguire supporta un'opzione verbose, propagare l'opzione verbose allo strumento.

#### <a name="--dry-run-switch"></a>--opzione di esecuzione a secco

Comandi echo Tool che verrebbero eseguiti, ma non eseguono alcun strumento.

#### <a name="additional-command-line-arguments"></a>Argomenti aggiuntivi della riga di comando

L'utilizzo di un oggetto `<arg>` che include uno spazio nel suo valore deve includere una coppia aggiuntiva di virgolette precedute.

```console
devinit run -t <toolname> -<somearg> "<some value>"
```

Per l'installazione di DotNet in una directory specifica `C:\Program Files\dotnet` :

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
| -t,--strumento      | Sì      | Obbligatorio. Nome dello strumento.                                                             |

Stampa le informazioni della Guida per uno strumento specifico.

## <a name="version"></a>Versione

```console
devinit version
```

Stampa le informazioni sulla versione corrente per devinilt.

## <a name="help"></a>Guida

```console
devinit help
devinit help list
```

Stampa il testo della Guida per il comando devinilt o per un comando specifico `devinit <command>` .
 
