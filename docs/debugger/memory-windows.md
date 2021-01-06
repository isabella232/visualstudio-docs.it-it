---
title: Visualizzazione della memoria per le variabili nel debugger | Microsoft Docs
description: Informazioni su come usare le finestre di memoria durante il debug per visualizzare lo spazio di memoria usato dall'app. Altre finestre mostrano le variabili e la posizione in cui risiedono nella memoria.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c39024e32c899310b88c1b0583d5b292b063937
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903110"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Usare le finestre di memoria nel debugger di Visual Studio (C#, C++, Visual Basic, F #)

Durante il debug, la finestra **memoria** Mostra lo spazio di memoria usato dall'app.

Le finestre del debugger come **espressioni di controllo**, **auto**, variabili **locali** e la finestra di dialogo controllo **immediato** mostrano le variabili, archiviate in posizioni specifiche in memoria. Nella finestra **memoria** viene visualizzata l'immagine complessiva. La visualizzazione della memoria è utile per l'analisi di grandi quantità di dati (ad esempio, buffer o stringhe di grandi dimensioni) che non vengono visualizzati correttamente nelle altre finestre.

La finestra **memoria** non è limitata alla visualizzazione dei dati. Vengono visualizzati tutti gli elementi nello spazio di memoria, inclusi i dati, il codice e i bit casuali del Garbage Collector nella memoria non assegnata.

La finestra **memoria** non è disponibile per il debug di script o SQL. Tali lingue non riconoscono il concetto di memoria.

## <a name="open-a-memory-window"></a>Aprire una finestra memoria

Analogamente ad altre finestre del debugger, le finestre di **memoria** sono disponibili solo durante una sessione di debug.

>[!IMPORTANT]
>Per abilitare le finestre della **memoria** , è necessario selezionare **Abilita debug a livello di indirizzo** in **strumenti**  >  **Opzioni** (o opzioni di **debug**  >  ) > **debug**  >  **generale**.

**Per aprire una finestra Memoria**

1. Assicurarsi che **Abilita debug a livello di indirizzo** sia selezionato in  >  **Opzioni** strumenti (o opzioni di **debug**  >  ) > **debug**  >  **generale**.

1. Avviare il debug selezionando la freccia verde, premendo **F5** o scegliendo **debug**  >  **Avvia debug**.

2. In **debug**  >    >  **memoria** Windows selezionare **memoria 1**, **memoria 2**, **memoria 3** o **memoria 4**. (Alcune edizioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offrono una sola finestra di **memoria** ).

## <a name="move-around-in-the-memory-window"></a>Spostarsi nella finestra memoria

Lo spazio degli indirizzi di un computer è grande ed è possibile perdere facilmente il posto scorrendo nella finestra **memoria** .

Gli indirizzi di memoria superiori vengono visualizzati nella parte inferiore della finestra. Per visualizzare un indirizzo superiore, scorrere verso il basso. Per visualizzare un indirizzo inferiore, scorrere verso l'alto.

È possibile passare immediatamente a un indirizzo specificato nella finestra **memoria** tramite il trascinamento della selezione oppure immettendo l'indirizzo nel campo **Indirizzo** . Il campo **Address** accetta indirizzi alfanumerici ed espressioni che restituiscono indirizzi, ad esempio `e.User.NonroamableId` .

Per forzare nuovamente la valutazione immediata di un'espressione nel campo **Indirizzo** , selezionare l'icona di rivalutazione **automatica** della freccia arrotondata.

Per impostazione predefinita, la finestra di **memoria** considera le espressioni di **Indirizzo** come espressioni Live, che vengono rivalutate durante l'esecuzione dell'app. Le espressioni Live possono essere utili, ad esempio, per visualizzare la memoria interessata da una variabile del puntatore.

**Per usare il trascinamento della selezione per spostarsi in una posizione di memoria:**

1. In qualsiasi finestra del debugger selezionare un indirizzo di memoria o una variabile puntatore che contenga un indirizzo di memoria.

2. Trascinare e rilasciare l'indirizzo o il puntatore nella finestra **memoria** . Tale indirizzo viene quindi visualizzato nel campo **Indirizzo** e la finestra **memoria** viene regolata in modo da visualizzare l'indirizzo nella parte superiore.

**Per spostarsi in una posizione di memoria inserendola nel campo Indirizzo:**

- Digitare o incollare l'indirizzo o l'espressione nel campo **Indirizzo** e premere **invio** oppure selezionarlo nell'elenco a discesa nel campo **Indirizzo** . La finestra **memoria** viene modificata in modo da visualizzare l'indirizzo nella parte superiore.

## <a name="customize-the-memory-window"></a>Personalizzare la finestra memoria

Per impostazione predefinita, il contenuto della memoria viene visualizzato come Integer a 1 byte in formato esadecimale e la larghezza della finestra determina il numero di colonne visualizzate. È inoltre possibile personalizzare il modo in cui il contenuto della memoria viene visualizzato nella finestra **Memoria**.

**Per cambiare il formato del contenuto della memoria:**

- Fare clic con il pulsante destro del mouse nella finestra **memoria** e scegliere i formati desiderati dal menu di scelta rapida.

**Per modificare il numero di colonne nella finestra memoria:**

- Selezionare la freccia a discesa accanto al campo **colonne** e selezionare il numero di colonne da visualizzare oppure selezionare **auto** per la regolazione automatica in base alla larghezza della finestra.

Se non si vuole modificare il contenuto della finestra di **memoria** durante l'esecuzione dell'app, è possibile disattivare la valutazione dell'espressione Live.

**Per attivare o disattivare la valutazione diretta:**

- Fare clic con il pulsante destro del mouse nella finestra **memoria** e scegliere **Rivaluta automaticamente** nel menu di scelta rapida.

  >[!NOTE]
  >La valutazione dell'espressione dinamica è un elemento di alternanza ed è attivata per impostazione predefinita, quindi la selezione di **Rivaluta automaticamente** lo disattiva. Se si seleziona nuovamente **rivalutazione** , viene nuovamente attivata.

È possibile nascondere o visualizzare la barra degli strumenti nella parte superiore della finestra **Memoria**. Quando la barra degli strumenti è nascosta, non sarà possibile accedere al campo dell' **Indirizzo** o ad altri strumenti.

**Per abilitare o disabilitare la visualizzazione della barra degli strumenti:**

- Fare clic con il pulsante destro del mouse nella finestra **memoria** e scegliere **Mostra barra degli strumenti** nel menu di scelta rapida. La barra degli strumenti verrà visualizzata o nascosta, a seconda del precedente stato.

## <a name="follow-a-pointer-through-memory"></a>Segui un puntatore tramite memoria

Nelle app in codice nativo, è possibile usare i nomi di registro come espressioni Live. È possibile, ad esempio, utilizzare il puntatore dello stack per seguire lo stack.

**Per osservare il movimento di un puntatore in memoria:**

1. Nel campo **Indirizzo** della finestra **memoria** immettere un'espressione puntatore nell'ambito corrente. A seconda del linguaggio, può essere necessario dereferenziarla.

2. Premere **INVIO**.

   Quando si usa un comando di debug, ad esempio **Step**, l'indirizzo di memoria visualizzato nel campo **Address** e nella parte superiore della finestra **Memory** viene modificato automaticamente quando cambia il puntatore.

## <a name="see-also"></a>Vedere anche
- [Visualizzare i dati nel debugger](../debugger/viewing-data-in-the-debugger.md)