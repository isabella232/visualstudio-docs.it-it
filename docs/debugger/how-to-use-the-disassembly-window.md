---
title: Visualizzare il Disassembly codice nel Debugger di Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/30/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51510d09a1840035bb96817d30aebdcd6bf3ebd7
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671144"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Visualizzare il codice disassembly del debugger di Visual Studio

Il **Disassembly** finestra Mostra il codice assembly corrispondente alle istruzioni create dal compilatore. Se si esegue il debug di codice gestito, queste istruzioni di assembly corrispondono al codice nativo creato dal compilatore Just-in-Time (JIT), non il Microsoft intermediate language (MSIL) creato dal compilatore di Visual Studio.  
  
> [!NOTE]
> Per sfruttare appieno le **Disassembly** finestra comprendere o nozioni di base [programmazione in linguaggio assembly](https://wikipedia.org/wiki/Assembly_language).
  
Questa funzionalità è disponibile solo se è abilitato il debug a livello di indirizzo. Non è disponibile per uno script o il debug SQL. 

Oltre alle istruzioni dell'assembly, il **Disassembly** finestra è possibile visualizzare le informazioni facoltative seguenti:  
  
- L'indirizzo di memoria in cui si trova ciascuna istruzione. Per le applicazioni native, è l'indirizzo di memoria effettiva. Per Visual Basic, C#, o codice gestito, si tratta di un offset dall'inizio della funzione.  
  
- Codice sorgente dal quale deriva il codice assembly.  
  
- Il codice byte, vale a dire le rappresentazioni in byte del computer effettivo o istruzioni MSIL.  
  
- Nomi di simboli per gli indirizzi di memoria.  
  
- Numeri di riga corrispondenti al codice sorgente.  
  
Le istruzioni in linguaggio assembly sono costituiti *mnemonici*, che sono abbreviazioni per i nomi di istruzioni, e *simboli* per variabili, registri e costanti. Ogni istruzione in linguaggio macchina è rappresentato da un elemento mnemonico in linguaggio assembly seguito facoltativamente da uno o più simboli.  
  
Il codice assembly si basa principalmente sui registri del processore o, per il codice gestito, registri di common language runtime. È possibile usare la **Disassembly** finestra lungo con la **registra** finestra, che consente di esaminare il contenuto del registro.  
  
Per visualizzare le istruzioni di codice macchina nel loro formato numerico non elaborato, anziché come linguaggio assembly, usare il **memoria** finestra o selezionare **byte del codice** dal menu di scelta rapida di **Disassembly**  finestra.  
  
## <a name="use-the-disassembly-window"></a>Utilizzare la finestra Disassembly

Per abilitare il **Disassembly** finestra, sotto **Tools** > **opzioni** (o **strumenti**  >  **Le opzioni**) > **Debugging**, selezionare **Abilita debug a livello di indirizzo**.

Per aprire la **Disassembly** finestra durante il debug, seleziona **Windows** > **Disassembly** oppure premere **Alt** + **8**.

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
Per abilitare informazioni facoltative o disabilitare, fare doppio clic nella **Disassembly** finestra e selezionare o deselezionare le opzioni desiderate nel menu di scelta rapida.  

Una freccia gialla nel margine sinistro contrassegna il punto di esecuzione corrente. Per il codice nativo, il punto di esecuzione corrisponde al contatore di programma della CPU. Questo indicatore mostra l'istruzione successiva che verrà eseguita dal programma.  

## <a name="see-also"></a>Vedere anche  

* [Spostamento verso l'alto o verso il basso in memoria](../debugger/how-to-page-up-or-down-in-memory.md)
* [Visualizzazione dei dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
* [Procedura: usare la finestra registri](../debugger/how-to-use-the-registers-window.md)
