---
title: Visualizzare lo stack di chiamate nel debugger | Microsoft Docs
description: Usare la finestra Stack di chiamate per visualizzare le chiamate di funzione o routine attualmente presenti nello stack Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: how-to
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c8c4044e88150aa40b5ae9fe89c43b3a4d8eaddc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154057"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Visualizzare lo stack di chiamate e usare la finestra Stack di chiamate nel debugger

Tramite la finestra **Stack di chiamate** è possibile visualizzare le chiamate di funzione o di routine attualmente presenti nello stack. La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

Quando [i simboli di](#bkmk_symbols) debug non sono disponibili per parte di uno stack di chiamate, la finestra **Stack** di chiamate potrebbe non essere in grado di visualizzare le informazioni corrette per tale parte dello stack di chiamate, visualizzando invece:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella presente Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**.  Vedere [Impostazioni di reimpostazione](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Visualizzare lo stack di chiamate nel debugger

- Durante il debug, nel menu **Debug** selezionare **Windows > Stack di chiamate**.

  ![Finestra Stack di chiamate](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Lo stack frame in cui è attualmente posizionato il puntatore di esecuzione è contraddistinto da una freccia gialla. Per impostazione predefinita, stack frame le informazioni di questo tipo vengono visualizzate nelle finestre di **origine,** Variabili locali, **Auto,** **Espressioni** di controllo **e Disassembly.** Per modificare il contesto del debugger in un altro frame nello stack, [passare a un](#bkmk_switch)altro stack frame .

## <a name="display-non-user-code-in-the-call-stack-window"></a>Visualizzare il codice non utente nella finestra Stack di chiamate

- Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Mostra codice esterno**.

Il codice non utente è qualsiasi codice che non viene visualizzato [quando](../debugger/just-my-code.md) Just My Code è abilitato. Nel codice gestito i frame di codice non utente sono nascosti per impostazione predefinita. Al posto dei frame di codice non utente viene visualizzata la notazione seguente:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Passare a un altro stack frame (modificare il contesto del debugger)

1. Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla stack frame di cui si desidera visualizzare il codice e i dati.

    In caso contrario, è possibile fare doppio clic su un frame nella finestra **Stack di** chiamate per passare a tale frame.

2. Selezionare **Passa al frame**.

     Accanto alla freccia verde con una coda a forma di graffa viene visualizzata stack frame selezionata. Il puntatore di esecuzione rimarrà nel frame originale, sempre contrassegnato dalla freccia gialla. Se si sceglie **Esegui** o **Continua** dal menu **Debug**, l'esecuzione continuerà nel frame originale, non nel frame selezionato.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Visualizzare il codice sorgente per una funzione nello stack di chiamate

- Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si vuole esaminare il codice sorgente e selezionare **Vai a codice sorgente**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Eseguire a una funzione specifica dalla finestra Stack di chiamate

- Nella finestra **Stack di chiamate** selezionare la funzione, fare clic con il pulsante destro del mouse e scegliere Esegui fino al **cursore**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Impostare un punto di interruzione nel punto di uscita di una chiamata di funzione

- Vedere [Impostare un punto di interruzione in una funzione dello stack di chiamate](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Visualizzare le chiamate a o da un altro thread

- Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Includi chiamate da e verso altri thread**.

## <a name="visually-trace-the-call-stack"></a>Tracciare visivamente lo stack di chiamate

In Visual Studio Enterprise (solo) è possibile visualizzare le mappe codice per lo stack di chiamate durante il debug.

- Nella finestra **Stack di chiamate** aprire il menu di scelta rapida. Scegliere **Mostra stack di chiamate sulla mappa codice** (**CTRL**  +  **MAIUSC**  +  **`** ).

    Per altre informazioni, vedere [Eseguire il mapping dei metodi nello stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)di .

![Mostra stack di chiamate sulla mappa codice](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Visualizzare il codice disassembly per una funzione nello stack di chiamate (C#, C++, Visual Basic, F#)

- Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si desidera esaminare il codice del disassembly e selezionare **Vai a disassembly**.

## <a name="change-the-optional-information-displayed"></a>Modificare le informazioni facoltative visualizzate

- Fare clic con il pulsante destro del **mouse nella finestra Stack di** chiamate e impostare o **deselezionare Mostra \<**_the information that you want_**>**.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a>Caricare i simboli per un modulo (C#, C++, Visual Basic, F#)

Nella finestra **Stack di chiamate** è possibile caricare i simboli di debug per un codice che non ne dispone. Questi simboli possono essere simboli .NET o di sistema scaricati dai server di simboli pubblici Microsoft o simboli in un percorso di simboli nel computer di cui si esegue il debug.

Vedere [Specificare il simbolo (con estensione pdb) e i file di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

### <a name="to-load-symbols"></a>Per caricare i simboli

1. Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sull stack frame per cui non vengono caricati i simboli. Il frame verrà disattivato (rappresentato in grigio).

2. Scegliere Carica **simboli e** quindi selezionare Server di **simboli Microsoft** (se disponibile) o passare al percorso dei simboli.

### <a name="to-set-the-symbol-path"></a>Per impostare il percorso dei simboli

1. Nella finestra **Stack di chiamate** scegliere **Impostazioni simboli** nel menu di scelta rapida.

     Viene visualizzata la finestra di dialogo **Opzioni** con la pagina **Simboli**.

2. Selezionare **Simbolo Impostazioni**.

3. Nella finestra di dialogo **Opzioni** fare clic sull'icona della cartella.

     Viene visualizzato un cursore nella casella **Percorsi dei file di simboli (pdb)**.

4. Immettere un percorso di directory nel percorso del simbolo nel computer di cui si esegue il debug. Per il debug locale e remoto, si tratta di un percorso nel computer locale.

5. Selezionare **OK** per chiudere la **finestra di dialogo** Opzioni.

## <a name="see-also"></a>Vedi anche

- [Codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Visualizzazione dei dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Specificare il simbolo (con estensione pdb) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Uso dei punti di interruzione](../debugger/using-breakpoints.md)