---
title: Comandi
description: Informazioni sui vari comandi a cui si ha accesso in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 180852e2895318f1ffc2fbf411c3945373b5ab4c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628565"
---
# <a name="visual-studio-commands"></a>Comandi di Visual Studio

È possibile immettere i comandi di Visual Studio nella finestra **Comando**, nella finestra **Comando immediato** o nella casella **Trova/Comando**. In ogni caso, per indicare che deve essere eseguito un comando anziché un'operazione di ricerca o di debug, viene usato il segno di maggiore (`>`).

È possibile trovare l'elenco completo dei comandi e la relativa sintassi nella pagina **Tastiera** in **Strumenti** > **Opzioni** > **Ambiente**.

Nelle versioni localizzate dell'IDE, i nomi di comandi possono essere immessi sia nella lingua locale dell'IDE sia in lingua inglese. È possibile ad esempio digitare `File.NewFile` o `Fichier.NouveauFichier` nell'IDE francese per eseguire lo stesso comando.

A molti comandi sono associati alias. Per un elenco di alias dei comandi, vedere [Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md). Per i tasti di scelta rapida dei comandi, vedere [Tasti di scelta rapida predefiniti in Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Carattere di escape

Il carattere di escape per i comandi di Visual Studio è l'accento circonflesso (^). Il carattere di escape indica che il carattere immediatamente successivo viene interpretato letteralmente e non come carattere di controllo. In questo modo, è possibile incorporare virgolette diritte ("), spazi, barre iniziali, accenti circonflessi o qualsiasi altro carattere letterale nel valore di un parametro o di un'opzione, ad eccezione dei nomi di opzioni. Ad esempio:

```
>Edit.Find ^^t /regex
```

L'accento circonflesso presenta lo stesso funzionamento sia all'interno sia all'esterno delle virgolette. Se corrisponde all'ultimo carattere sulla riga, viene ignorato.

## <a name="commands-with-arguments"></a>Comandi con argomenti

I comandi seguenti accettano opzioni o argomenti:

| Nome comando | Descrizione |
| - | - |
| [Aggiungi elemento esistente](../../ide/reference/add-existing-item-command.md) | Aggiunge un file esistente alla soluzione corrente e lo apre. |
| [Aggiungi progetto esistente](../../ide/reference/add-existing-project-command.md) | Aggiunge un progetto esistente alla soluzione corrente. |
| [Aggiungi nuovo elemento](../../ide/reference/add-new-item-command.md) | Aggiunge un nuovo elemento, ad esempio un file con estensione htm, css o txt o una pagina con frame, alla soluzione corrente e lo apre. |
| [Alias](../../ide/reference/alias-command.md) | Crea un nuovo alias per un comando completo, per un comando completo con i relativi argomenti oppure per un altro alias. |
| [Valuta istruzione](../../ide/reference/evaluate-statement-command.md) | Valuta e visualizza l'istruzione specificata. |
| [Find](../../ide/reference/find-command.md) | Ricerca il testo nei file usando un subset delle opzioni disponibili nel comando **Trova e sostituisci** . |
| [Cerca nei file](../../ide/reference/find-in-files-command.md) | Ricerca il testo nei file usando un subset delle opzioni disponibili nel comando [Cerca nei file](../../ide/find-in-files.md). |
| [Vai a](../../ide/reference/go-to-command.md) | Sposta il cursore sulla riga specificata. |
| [Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md) | Visualizza lo stack di chiamate corrente. |
| [Elenca disassembly](../../ide/reference/list-disassembly-command.md) | Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori. |
| [Elenca memoria](../../ide/reference/list-memory-command.md) | Visualizza il contenuto dell'intervallo di memoria specificato. |
| [Elencare i moduli](../../ide/reference/list-modules-command.md) | Elenca i moduli disponibili per il processo corrente. |
| [Elenca registri](../../ide/reference/list-registers-command.md) | Visualizza un elenco di registri. |
| [Elenca origine](../../ide/reference/list-source-command.md) | Visualizza le righe del codice sorgente specificate. |
| [Elenca thread](../../ide/reference/list-threads-command.md) | Visualizza un elenco dei thread del programma corrente. |
| [Registra output finestra di comando](../../ide/reference/log-command-window-output-command.md) | Copia interamente l'input e l'output della finestra di comando in un file. |
| [Nuovo file](../../ide/reference/new-file-command.md) | Crea un nuovo file e lo aggiunge al progetto attualmente selezionato. |
| [Apri file](../../ide/reference/open-file-command.md) | Apre un file esistente e consente di specificare un editor. |
| [Aprire Project](../../ide/reference/open-project-command.md) | Apre un progetto esistente e consente di aggiungerlo alla soluzione corrente. |
| [Stampa](../../ide/reference/print-command.md) | Valuta l'espressione e visualizza i risultati o il testo specificato. |
| [Comando Controllo rapido](../../ide/reference/quick-watch-command.md) | Visualizza il testo selezionato o specificato nel campo **Espressione** della finestra di dialogo **Espressione di controllo rapida** . |
| [Replace](../../ide/reference/replace-command.md) | Sostituisce elementi di testo nei file usando un subset delle opzioni disponibili nel comando **Trova e sostituisci** . |
| [Sostituisci nei file](../../ide/reference/replace-in-files-command.md) | Sostituisce elementi di testo nei file usando un subset delle opzioni disponibili nella [Sostituisci nei file](../../ide/replace-in-files.md). |
| [Imposta stack frame corrente](../../ide/reference/set-current-stack-frame-command.md) | Consente di visualizzare uno specifico stack frame. |
| [Imposta thread corrente](../../ide/reference/set-current-thread-command.md) | Consente di visualizzare un thread specifico. |
| [Imposta radice](../../ide/reference/set-radix-command.md) | Determina il numero di byte da visualizzare. |
| [Shell](../../ide/reference/shell-command.md) | Avvia i programmi da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come se il comando venisse eseguito dal prompt dei comandi. |
| [Comando ShowWebBrowser](../../ide/reference/showwebbrowser-command.md) | Visualizza l'URL specificato in una finestra del Web browser all'interno o all'esterno dell'ambiente di sviluppo integrato (IDE). |
| [Inizia](../../ide/reference/start-command.md) | Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori. |
| [Percorso](../../ide/reference/symbol-path-command.md) | Imposta l'elenco delle directory in cui il debugger deve eseguire la ricerca dei simboli. |
| [Attiva/disattiva punto di interruzione](../../ide/reference/toggle-breakpoint-command.md) | Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file. |
| [Comando Watch](../../ide/reference/watch-command.md) | Crea e apre un'istanza specificata di una finestra **Espressione di controllo** . |

## <a name="see-also"></a>Vedi anche

- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
