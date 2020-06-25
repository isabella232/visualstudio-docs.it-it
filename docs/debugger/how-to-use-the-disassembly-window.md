---
title: Visualizzare il codice disassembly nel debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 10/30/2018
ms.topic: how-to
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0570aec5e8571e75cf64418a2c8c7c95cf507d31
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348704"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visualizzare il codice disassembly nel debugger di Visual Studio (C#, C++, Visual Basic, F #)

Nella finestra **Disassembly** viene visualizzato il codice assembly corrispondente alle istruzioni create dal compilatore. Se si sta eseguendo il debug di codice gestito, queste istruzioni di assembly corrispondono al codice nativo creato dal compilatore JIT (just-in-Time), non al linguaggio MSIL (Microsoft Intermediate Language) creato dal compilatore di Visual Studio.

> [!NOTE]
> Per sfruttare appieno la finestra **Disassembly** , comprendere o apprendere le nozioni di base della [programmazione in linguaggio assembly](https://wikipedia.org/wiki/Assembly_language).

Questa funzionalità è disponibile solo se è abilitato il debug a livello di indirizzo. Non è disponibile per il debug di script o SQL.

Oltre alle istruzioni in linguaggio assembly, nella finestra **Disassembly** è possibile visualizzare le informazioni facoltative seguenti:

- L'indirizzo di memoria in cui si trova ciascuna istruzione. Per le applicazioni native, è l'indirizzo di memoria effettivo. Per Visual Basic o C#, si tratta di un offset dall'inizio della funzione.

- Codice sorgente dal quale deriva il codice assembly.

- Byte di codice, ovvero le rappresentazioni in byte del computer o delle istruzioni MSIL effettive.

- Nomi di simboli per gli indirizzi di memoria.

- Numeri di riga corrispondenti al codice sorgente.

Le istruzioni in linguaggio assembly sono costituite da *tasti*di scelta, ovvero abbreviazioni per i nomi di istruzioni e *simboli* per variabili, registri e costanti. Ogni istruzione in linguaggio computer è rappresentata da un tasto di scelta rapida in linguaggio assembly, seguito facoltativamente da uno o più simboli.

Il codice assembly si basa principalmente sui registri del processore o, per il codice gestito, Common Language Runtime registri. È possibile utilizzare la finestra **Disassembly** insieme alla finestra **registri** , che consente di esaminare il contenuto del registro.

Per visualizzare le istruzioni del codice del computer nel formato numerico non elaborato, anziché come linguaggio assembly, utilizzare la finestra **memoria** o selezionare **byte di codice** dal menu di scelta rapida nella finestra **Disassembly** .

## <a name="use-the-disassembly-window"></a>Usare la finestra Disassembly

Per abilitare la finestra **Disassembly** , in **strumenti**  >  **Opzioni** (o opzioni **strumenti**  >  **Options**) > **debug**selezionare **Abilita debug a livello di indirizzo**.

Per aprire la finestra **Disassembly** durante il debug, selezionare **Windows**  >  **Disassembly** di Windows o premere **ALT** + **8**.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Per attivare o disattivare le informazioni facoltative, fare clic con il pulsante destro del mouse nella finestra **Disassembly** e impostare o deselezionare le opzioni desiderate nel menu di scelta rapida.

Una freccia gialla nel margine sinistro contrassegna il punto di esecuzione corrente. Per il codice nativo, il punto di esecuzione corrisponde al contatore di programma della CPU. Questo indicatore mostra l'istruzione successiva che verrà eseguita dal programma.

## <a name="see-also"></a>Vedi anche

* [Procedura: Spostare verso l'alto o verso il basso una pagina di memoria](../debugger/how-to-page-up-or-down-in-memory.md)
* [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
* [Procedura: utilizzare la finestra registri](../debugger/how-to-use-the-registers-window.md)