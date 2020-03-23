---
title: Trovare l'attività di debug
description: Identificare la funzionalità del debugger che consente di eseguire il debug dell'appIdentify the debugger feature that will help you debug your app
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302182"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Trovare l'attività di debug in Visual StudioFind your debugging task in Visual Studio

Per informazioni utili per eseguire il mapping dell'attività di debug alla funzionalità corretta del debugger di Visual Studio pertinente, utilizzare i collegamenti forniti in questo articolo. L'elenco delle attività qui include attività comuni, ad esempio la sospensione del codice per il debug, il controllo delle variabili e l'invio di messaggi alla finestra **di output.** Se è necessaria una panoramica delle funzionalità del debugger, vedere [Prima occhiata al debugger.](debugger-feature-tour.md)

## <a name="pause-running-code"></a>Sospendere il codice in esecuzione

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Sospendere il codice in esecuzione per esaminare una riga di codice che potrebbe contenere un bug

Impostare un punto di interruzione. Per ulteriori informazioni, vedere [Utilizzo dei punti di interruzione](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Sospendere ed esaminare l'app quando raggiunge uno stato specifico

Provare un punto di interruzione condizionale per controllare dove e quando un punto di interruzione viene attivato utilizzando la logica condizionale. Per ulteriori informazioni, vedere [Condizioni dei punti di interruzione](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Sospendere il codice solo quando la proprietà o il valore di un oggetto specifico viene modificato

Impostare un punto di interruzione di dati per il [linguaggio](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)C. 
::: moniker range=">= vs-2019"
Per le app che usano .NET Core 3, è anche possibile impostare un punto di interruzione dei [dati.](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)
::: moniker-end

In caso contrario, solo per c'è e F, è possibile [tenere traccia di un ID oggetto con un punto di interruzione condizionale.](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Sospendere il codice all'interno di un ciclo in corrispondenza di una determinata iterazione

Impostare un punto di interruzione usando **il numero di passaggi** come condizione. Per ulteriori informazioni, consultate [Conteggio passaggi](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Sospendere il codice all'inizio di una funzione quando si conosce il nome della funzione ma non la relativa posizione

È possibile eseguire questa operazione con un punto di interruzione di funzione. Per ulteriori informazioni, consultate [Impostare i punti di interruzione delle funzioni.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Sospendere il codice all'inizio di più funzioni con lo stesso nome

Quando si dispone di più funzioni con lo stesso nome (funzioni in overload o funzioni in progetti diversi), è possibile utilizzare un [punto di interruzione](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)di funzione .

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Gestire e tenere traccia dei punti di interruzione

Utilizzare la finestra **Punti di interruzione.** Per ulteriori informazioni, consultate [Gestire i punti di interruzione.](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Sospendere il codice ed eseguire il debug quando viene generata un'eccezione gestita o non gestita specificaPause code and debug when a specific handled or unhandled exception is thrown

Sebbene l'helper eccezioni mostri dove si è verificato un errore, se si desidera sospendere ed eseguire il debug dell'errore specifico, è possibile [indicare al debugger di interrompersi quando viene generata un'eccezione](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Impostare un punto di interruzione dallo stack di chiamateSet a breakpoint from the call stack

Se si desidera sospendere ed eseguire il debug del codice durante l'esame del flusso di esecuzione o la visualizzazione delle funzioni nelle finestre **Stack** di chiamate, vedere [Impostare un punto di interruzione nella finestra Stack di chiamate](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Sospendere il codice in corrispondenza di un'istruzione di assembly specifica

A tale scopo, [impostare un punto di interruzione dalla finestra Disassembly](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Esegui codice

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Imparare i comandi per eseguire il codice un'istruzione alla volta durante il debugLearn the commands to step through your code while debugging

Per ulteriori informazioni, consultate [Esplorare il codice con il debugger.](navigating-through-code-with-the-debugger.md)

## <a name="inspect-data"></a>Esaminare i dati

### <a name="check-the-value-of-variables-while-running-your-app"></a>Controllare il valore delle variabili durante l'esecuzione dell'app

Posizionare il puntatore del mouse sulle variabili utilizzando [i suggerimenti dati](view-data-values-in-data-tips-in-the-code-editor.md) o controllare le variabili nella finestra Auto e variabili [locali](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Osservare il valore mutevole di una variabile specifica

Impostare un orologio sulla variabile. Per ulteriori informazioni, consultate [Impostare un controllo sulle variabili.](watch-and-quickwatch-windows.md)

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Visualizzare le stringhe troppo lunghe per la finestra del debuggerView strings that are oo long for the debugger window

Aprire il [visualizzatore di stringhe](view-strings-visualizer.md) incorporato durante il debug.

## <a name="configure-debugging"></a>Configurare il debug

### <a name="customize-information-shown-in-the-debugger"></a>Personalizzare le informazioni visualizzate nel debugger

È possibile visualizzare informazioni diverse dal tipo di oggetto come valore in diverse finestre del debugger. Per il codice di C, Visual Basic, F e C,/CLI, utilizzare l'attributo [DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Per opzioni più avanzate, è anche possibile personalizzare l'interfaccia utente creando un [visualizzatore personalizzato.](create-custom-visualizers-of-data.md)

Per il linguaggio nativo di C, utilizzare il [framework NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Configurare le impostazioni del debugger

Per configurare le opzioni del debugger e le impostazioni del progetto del debugger, vedere [Impostazioni e preparazione del](debugger-settings-and-preparation.md)debugger .

## <a name="additional-tasks"></a>Attività aggiuntive

### <a name="fix-an-exception"></a>Correggere un'eccezioneFix an exception

Consultate [Correggere un'eccezione.](write-better-code-with-visual-studio.md#fix-an-exception)

### <a name="edit-code-during-a-debugging-session"></a>Modificare il codice durante una sessione di debugEdit code during a debugging session

Utilizzare [Modifica e continuare](edit-and-continue.md). Per XAML, usa [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Inviare messaggi alla finestra output senza modificare il codice

Impostare un punto di analisi. Per ulteriori informazioni, vedere [Utilizzo dei punti di analisi](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Visualizzare l'ordine in cui vengono chiamate le funzioni

Vedere [Come visualizzare lo stack di chiamate](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Eseguire il debug su computer remotiDebug on remote machines

Vedere [Debug remoto](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Eseguire il debug di un'app già in esecuzioneDebug an app that is already running

Vedere [Connettersi a un processo in esecuzione.](attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="debug-multithreaded-applications"></a>Eseguire il debug di applicazioni multithreading

Consultate [Eseguire il debug di applicazioni multithreading.](debug-multithreaded-applications-in-visual-studio.md)

### <a name="fix-performance-issues"></a>Correggi problemi di prestazioni

Vedere [Prima occhiata alle strumenti di profilatura](../profiling/profiling-feature-tour.md)