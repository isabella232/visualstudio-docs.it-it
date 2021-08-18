---
title: Visualizzare la memoria per le variabili nel debugger | Microsoft Docs
description: Informazioni su come usare le finestre memoria durante il debug per visualizzare lo spazio di memoria in uso dall'app. Altre finestre mostrano le variabili e la posizione in cui si trovano in memoria.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8a725ced36f886054094cc0ce97da34a1a74d3da
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090720"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Usare le finestre Memoria nel debugger Visual Studio (C#, C++, Visual Basic, F#)

Durante il debug, la **finestra Memoria** mostra lo spazio di memoria utilizzato dall'app.

Le finestre **del** **debugger,** ad esempio  Espressioni di controllo, **Auto,** Variabili locali e la finestra di dialogo Controllo immediato, mostrano le variabili, che vengono archiviate in posizioni specifiche in memoria. La **finestra Memoria** mostra l'immagine complessiva. La visualizzazione memoria è utile per esaminare grandi quantità di dati (buffer o stringhe di grandi dimensioni, ad esempio) che non vengono visualizzati bene nelle altre finestre.

La **finestra** Memoria non è limitata alla visualizzazione dei dati. Visualizza tutti gli elementi nello spazio di memoria, inclusi dati, codice e bit casuali di Garbage Collection nella memoria non assegnata.

La **finestra Memoria** non è disponibile per il debug SQL script. Questi linguaggi non riconoscono il concetto di memoria.

## <a name="open-a-memory-window"></a>Aprire una finestra Memoria

Analogamente ad altre finestre del debugger, le **finestre Memoria** sono disponibili solo durante una sessione di debug.

>[!IMPORTANT]
>Per abilitare le **finestre Memoria,** **è** necessario selezionare Abilita debug a livello di indirizzo **in** Opzioni degli strumenti (o Opzioni di  >     >  debug) > **Debug**  >  **generale**.

**Per aprire una finestra Memoria**

1. Assicurarsi che **l'opzione Abilita debug a livello** di indirizzo sia selezionata in Opzioni degli strumenti (o Opzioni di   >     >  debug) > **Debug**  >  **generale**.

1. Avviare il debug selezionando la freccia verde, premendo **F5** o selezionando **Debug**  >  **Avvia debug**.

2. In **Debug**  >  **Windows**  >  **memoria** selezionare **Memoria 1**, **Memoria 2**, **Memoria 3** o **Memoria 4**. Alcune edizioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offrono una sola finestra **memoria.**

## <a name="move-around-in-the-memory-window"></a>Spostarsi nella finestra Memoria

Lo spazio degli indirizzi di un computer è di grandi dimensioni ed è possibile perdere facilmente il proprio posto scorrendo nella **finestra** Memoria.

Gli indirizzi di memoria superiori vengono visualizzati nella parte inferiore della finestra. Per visualizzare un indirizzo superiore, scorrere verso il basso. Per visualizzare un indirizzo inferiore, scorrere verso l'alto.

È possibile passare immediatamente a un  indirizzo specificato nella finestra Memoria usando il trascinamento della selezione o immettendo l'indirizzo nel **campo** Indirizzo. Il **campo Address** accetta indirizzi alfanumerici ed espressioni che restituiscono indirizzi, ad esempio `e.User.NonroamableId` .

Per forzare la rivalutazione immediata di un'espressione nel campo **Indirizzo,** selezionare l'icona Rivaluta **automaticamente la freccia** arrotondata.

Per impostazione predefinita, la **finestra Memoria** considera le **espressioni Address** come espressioni live, che vengono valutate nuovamente durante l'esecuzione dell'app. Le espressioni live possono essere utili, ad esempio, per visualizzare la memoria toccata da una variabile puntatore.

**Per usare il trascinamento della selezione per spostarsi in una posizione di memoria:**

1. In qualsiasi finestra del debugger selezionare un indirizzo di memoria o una variabile puntatore contenente un indirizzo di memoria.

2. Trascinare l'indirizzo o il puntatore nella **finestra** Memoria. Tale indirizzo viene quindi visualizzato nel **campo Indirizzo** e la finestra **Memoria** viene adattata per visualizzare tale indirizzo nella parte superiore.

**Per passare a una posizione di memoria immetterla nel campo Indirizzo:**

- Digitare o incollare l'indirizzo o l'espressione nel campo **Indirizzo** e premere **INVIO** oppure sceglierlo nell'elenco a discesa nel **campo** Indirizzo. La **finestra Memoria** viene regolata per visualizzare l'indirizzo nella parte superiore.

## <a name="customize-the-memory-window"></a>Personalizzare la finestra Memoria

Per impostazione predefinita, il contenuto della memoria viene visualizzato come numeri interi a 1 byte in formato esadecimale e la larghezza della finestra determina il numero di colonne visualizzate. È inoltre possibile personalizzare il modo in cui il contenuto della memoria viene visualizzato nella finestra **Memoria**.

**Per cambiare il formato del contenuto della memoria:**

- Fare clic con il pulsante destro **del** mouse nella finestra Memoria e scegliere i formati desiderati dal menu di scelta rapida.

**Per modificare il numero di colonne nella finestra Memoria:**

- Selezionare la freccia a discesa accanto al campo **Colonne** e selezionare il numero di colonne da visualizzare oppure selezionare **Automatico** per la regolazione automatica in base alla larghezza della finestra.

Se non si vuole che il contenuto della **finestra** Memoria cambi durante l'esecuzione dell'app, è possibile disattivare la valutazione delle espressioni in tempo reale.

**Per attivare o disattivare la valutazione diretta:**

- Fare clic con il pulsante destro del mouse **nella** finestra Memoria e scegliere **Rivaluta automaticamente** nel menu di scelta rapida.

  >[!NOTE]
  >La valutazione delle espressioni in tempo reale è un interruttore e è attivata per impostazione predefinita, quindi selezionando **Rivaluta automaticamente** viene disattivata. Se **si seleziona Rivaluta automaticamente,** viene nuovamente attivata.

È possibile nascondere o visualizzare la barra degli strumenti nella parte superiore della finestra **Memoria**. Non sarà possibile accedere al campo **Indirizzo** o ad altri strumenti quando la barra degli strumenti è nascosta.

**Per attivare o disattivare la visualizzazione della barra degli strumenti:**

- Fare clic con il pulsante destro del **mouse nella** finestra Memoria e scegliere Mostra **barra degli** strumenti nel menu di scelta rapida. La barra degli strumenti verrà visualizzata o nascosta, a seconda del precedente stato.

## <a name="follow-a-pointer-through-memory"></a>Seguire un puntatore attraverso la memoria

Nelle app di codice nativo è possibile usare i nomi dei registri come espressioni in tempo reale. È possibile, ad esempio, utilizzare il puntatore dello stack per seguire lo stack.

**Per osservare il movimento di un puntatore in memoria:**

1. Nel campo **Indirizzo** della finestra **Memoria** immettere un'espressione puntatore nell'ambito corrente. A seconda del linguaggio, può essere necessario dereferenziarla.

2. Premere **INVIO**.

   Quando si usa un comando di debug, ad esempio **Passaggio**, l'indirizzo di memoria visualizzato nel campo **Indirizzo** e nella parte superiore della finestra Memoria cambia automaticamente quando cambia il puntatore. 

## <a name="see-also"></a>Vedi anche
- [Visualizzare i dati nel debugger](../debugger/viewing-data-in-the-debugger.md)