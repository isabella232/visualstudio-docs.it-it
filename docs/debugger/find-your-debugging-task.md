---
title: 'Domande frequenti: trovare la funzionalità di debug'
description: Domande frequenti che consentono di identificare la funzionalità del debugger che consente di eseguire il debug dell'app
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
ms.openlocfilehash: a34aa926fca081a498173cd5fcc439a6b3886ba7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728031"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Domande frequenti: trovare la funzionalità di debug necessaria in Visual Studio

Se è necessario assistenza per eseguire il mapping dell'attività di debug alla funzionalità corretta del debugger di Visual Studio pertinente, usare i collegamenti forniti in questo articolo. L'elenco di attività include attività comuni, ad esempio la sospensione del codice per il debug, il controllo delle variabili e l'invio di messaggi alla finestra di **output** . Se è necessaria una panoramica delle funzionalità del debugger, vedere [la prima occhiata al debugger](debugger-feature-tour.md) .

## <a name="fix-an-exception"></a>Correggi un'eccezione

- Vedere [correggere un'eccezione](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Sospendere il codice in esecuzione

- **Sospendere l'esecuzione del codice per esaminare una riga di codice che potrebbe contenere un bug**

  Impostare un punto di interruzione. Per ulteriori informazioni, vedere [utilizzo](using-breakpoints.md)di punti di interruzione.

- **Sospendere e controllare l'app quando raggiunge uno stato specifico**

  Provare un punto di interruzione condizionale per controllare dove e quando un punto di interruzione viene attivato utilizzando la logica condizionale. Per altre informazioni, vedere [condizioni](using-breakpoints.md#breakpoint-conditions)del punto di interruzione.

- **Sospendere il codice solo quando cambia la proprietà o il valore di un oggetto specifico**

  Per C++, impostare un punto di [interruzione dei dati](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  Per le app che usano .NET Core 3, è anche possibile impostare un punto di [interruzione dei dati](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
  ::: moniker-end

  In caso contrario, solo per C# e F #, è possibile [tenere traccia di un ID oggetto con un punto di interruzione condizionale](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Sospendere il codice all'interno di un ciclo in una determinata iterazione**

  Impostare un punto di interruzione utilizzando il **numero di passaggi** come condizione. Per ulteriori informazioni, vedere [passaggi](using-breakpoints.md#set-a-hit-count-condition).

- **Sospendere il codice all'inizio di una funzione quando si conosce il nome della funzione, ma non la relativa posizione**

  Questa operazione può essere eseguita con un punto di interruzione di funzione. Per altre informazioni, vedere [impostare](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)i punti di interruzione di una funzione.

- **Sospende il codice all'inizio di più funzioni con lo stesso nome**

  Quando si hanno più funzioni con lo stesso nome (funzioni o funzioni in overload in progetti diversi), è possibile usare un punto di [interruzione della funzione](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Gestisci e tieni traccia dei punti di interruzione**

  Utilizzare la finestra punti di **interruzione** . Per altre informazioni, vedere [gestire](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_)i punti di interruzione.

- **Sospendere il codice ed eseguire il debug quando viene generata un'eccezione gestita o non gestita specifica**

  Sebbene l'helper eccezioni indichi dove si è verificato un errore, se si desidera sospendere ed eseguire il debug dell'errore specifico, è possibile [indicare al debugger di interrompere l'interruzione quando viene generata un'eccezione](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Impostare un punto di interruzione dallo stack di chiamate**

  Per sospendere ed eseguire il debug del codice durante l'analisi del flusso di esecuzione o la visualizzazione delle funzioni nelle finestre **dello stack di chiamate** , vedere [impostare un punto di interruzione nella finestra stack di chiamate](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Sospendere il codice in corrispondenza di un'istruzione di assembly specifica**

  A tale scopo, è possibile [impostare un punto di interruzione dalla finestra Disassembly](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Esegui codice

- **Informazioni sui comandi per eseguire un'istruzione alla volta nel codice durante il debug**

  Per altre informazioni, vedere [spostarsi nel codice con il debugger](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Esaminare i dati

- **Controllare il valore delle variabili durante l'esecuzione dell'app**

  Passare il mouse sulle variabili usando [suggerimenti dati](view-data-values-in-data-tips-in-the-code-editor.md) o [controllare le variabili nella finestra auto e variabili locali](autos-and-locals-windows.md).

- **Osservare il valore di modifica di una variabile specifica**

  Impostare un'espressione di controllo sulla variabile. Per altre informazioni, vedere [impostare un'espressione di controllo sulle variabili](watch-and-quickwatch-windows.md).

- **Visualizzare le stringhe troppo lunghe per la finestra del debugger**

  Aprire il [Visualizzatore di stringhe](view-strings-visualizer.md) predefinito durante il debug.

## <a name="debug-an-app-that-is-already-running"></a>Eseguire il debug di un'app già in esecuzione

- Vedere [Connetti a un processo in esecuzione](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Eseguire il debug di applicazioni multithreading

- Vedere [eseguire il debug di applicazioni multithread](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Configurare il debug

- **Configurare le impostazioni del debugger**

  Per configurare le opzioni del debugger e le impostazioni del progetto del debugger, vedere [Impostazioni e preparazione del debugger](debugger-settings-and-preparation.md).

- **Personalizzare le informazioni visualizzate nel debugger**

  Potrebbe essere necessario visualizzare informazioni diverse dal tipo di oggetto come valore in finestre del debugger diverse. Per il codice C#, Visual Basic, F # e C++/CLI, usare l'attributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Per le opzioni più avanzate, è anche possibile personalizzare l'interfaccia utente creando un [visualizzatore personalizzato](create-custom-visualizers-of-data.md).

  Per il linguaggio C++ nativo, usare il [Framework NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Attività aggiuntive

- **Modificare il codice durante una sessione di debug**

  Usare [modifica e continuazione](edit-and-continue.md). Per XAML, usare il [ricaricamento a caldo di XAML](../xaml-tools/xaml-hot-reload.md).

- **Invia messaggi alla finestra di output senza modificare il codice**

  Impostare un punto di analisi. Per altre informazioni, vedere [uso di punti](using-tracepoints.md).

- **Consente di visualizzare l'ordine in cui vengono chiamate le funzioni**

  Vedere [come visualizzare lo stack di chiamate](how-to-use-the-call-stack-window.md).

- **Eseguire il debug su computer remoti**

  Vedere [Debug remoto](remote-debugging.md).

- **Correggere i problemi di prestazioni**

  Vedere [prima di tutto gli strumenti di profilatura](../profiling/profiling-feature-tour.md)
