---
title: Visualizzare il codice disassembly nel debugger | Microsoft Docs
description: Usare la finestra Disassembly in Visual Studio per visualizzare il codice dell'assembly corrispondente alle istruzioni create dal compilatore.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cc563c6ffc7a97af684edb49b9bb7466ed7bd24a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051846"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visualizzare il codice disassembly nel debugger Visual Studio (C#, C++, Visual Basic, F#)

Nella finestra **Disassembly** viene visualizzato il codice assembly corrispondente alle istruzioni create dal compilatore. Se si esegue il debug di codice gestito, queste istruzioni dell'assembly corrispondono al codice nativo creato dal compilatore JIT (Just-In-Time), non al linguaggio MSIL (Microsoft Intermediate Language) creato dal compilatore Visual Studio.

> [!NOTE]
> Per sfruttare al meglio la finestra **Disassembly,** comprendere o apprendere le nozioni di base della programmazione [in linguaggio assembly](https://wikipedia.org/wiki/Assembly_language).

Questa funzionalità è disponibile solo se è abilitato il debug a livello di indirizzo. Non è disponibile per il debug di script o SQL debug.

Oltre alle istruzioni in linguaggio assembly, nella finestra **Disassembly** è possibile visualizzare le informazioni facoltative seguenti:

- L'indirizzo di memoria in cui si trova ciascuna istruzione. Per le applicazioni native, è l'indirizzo di memoria effettivo. Per Visual Basic o C#, è un offset dall'inizio della funzione.

- Codice sorgente dal quale deriva il codice assembly.

- Byte di codice, cio, le rappresentazioni di byte del computer effettivo o istruzioni MSIL.

- Nomi di simboli per gli indirizzi di memoria.

- Numeri di riga corrispondenti al codice sorgente.

Le istruzioni in linguaggio assembly sono costituite da *mnemoniche*, che sono abbreviazioni per i nomi delle istruzioni e *simboli* per variabili, registri e costanti. Ogni istruzione del linguaggio macchina è rappresentata da un mnemoico del linguaggio assembly seguito facoltativamente da uno o più simboli.

Il codice assembly si basa in larga parte sui registri del processore o, per il codice gestito, sui registri di Common Language Runtime. È possibile usare la **finestra Disassembly** insieme alla **finestra Registri,** che consente di esaminare il contenuto del registro.

Per visualizzare le istruzioni del codice macchina nel formato numerico  non elaborato, anziché come linguaggio assembly, usare la finestra Memoria o selezionare **Byte** codice dal menu di scelta rapida nella **finestra Disassembly.**

## <a name="use-the-disassembly-window"></a>Usare la finestra Disassembly

Per abilitare la **finestra Disassembly,** in **Strumenti**  >  **Opzioni**  >  **debug** selezionare **Abilita debug a livello di indirizzo**.

Per aprire la **finestra Disassembly** durante il debug, **selezionare Windows**  >  **Disassembly** o premere **ALT** + **8**.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Per attivare o disattivare le informazioni facoltative, fare clic con il pulsante destro del mouse nella finestra **Disassembly** e impostare o deselezionare le opzioni desiderate nel menu di scelta rapida.

Una freccia gialla nel margine sinistro contrassegna il punto di esecuzione corrente. Per il codice nativo, il punto di esecuzione corrisponde al contatore del programma della CPU. Questo indicatore mostra l'istruzione successiva che verrà eseguita dal programma.

## <a name="see-also"></a>Vedi anche

* [Procedura: Spostare verso l'alto o verso il basso una pagina di memoria](../debugger/how-to-page-up-or-down-in-memory.md)
* [Visualizzazione dei dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
* [Procedura: Usare la finestra Registri](../debugger/how-to-use-the-registers-window.md)