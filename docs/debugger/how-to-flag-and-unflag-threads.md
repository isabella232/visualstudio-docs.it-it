---
title: Come contrassegnare e decontrassegnare i thread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7480f953e2fca57c296d6d1641059993bfa582c
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349627"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Procedura: contrassegnare e decontrassegnare i thread (C#, Visual Basic, C++)

È possibile contrassegnare un thread che si desidera prestare particolare attenzione contrassegnando il thread con un'icona nelle finestre **thread**, **stack in parallelo** (visualizzazione thread), espressione di controllo in **parallelo**e **thread GPU** . Questa icona può essere d'aiuto all'utente e ad altri per distinguere i thread con flag dagli altri thread.

I thread contrassegnati ricevono anche un trattamento speciale nell'elenco dei **thread** sulla barra degli strumenti **posizione di debug** e nelle altre finestre di debug multithread. È possibile visualizzare tutti i thread o solo i thread contrassegnati nell'elenco dei **thread** o nelle altre finestre.

### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread

- Nella finestra **thread** o espressione di **controllo in parallelo** individuare il thread a cui si è interessati e fare clic sull'icona del flag per selezionare o deselezionare il flag.
- Nella finestra **stack in parallelo** , fare clic con il pulsante destro del mouse su un thread o un gruppo di thread e selezionare **flag/ \<thread> ** o **Rimuovi flag/ \<thread> **.

### <a name="to-unflag-all-threads"></a>Per rimuovere i flag di tutti thread

- Nella finestra **Thread** fare clic con il pulsante destro del mouse su un thread qualsiasi, quindi scegliere **Rimuovi flag di tutti i thread**.
- Nella finestra espressione di **controllo in parallelo** selezionare tutti i thread contrassegnati, quindi fare clic con il pulsante destro del mouse e scegliere **Rimuovi flag**.

### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag

- Scegliere il pulsante **Mostra solo thread contrassegnati** in una delle finestre di debug multithread.

### <a name="to-flag-just-my-code"></a>Per contrassegnare Just My Code

1. Fare clic sull'icona del flag nella barra degli strumenti in cima alla finestra **Thread**.

2. Fare clic su **Contrassegna Just My Code** nell'elenco a discesa.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Per contrassegnare thread associati ai moduli selezionati

1. Fare clic sull'icona del flag nella barra degli strumenti della finestra **Thread**.

2. Fare clic su **Contrassegna selezione moduli personalizzata** nell'elenco a discesa.

3. Selezionare i moduli desiderati nella finestra di dialogo **Seleziona moduli**.

4. (Facoltativo) Digitare una stringa per cercare moduli specifici nella casella **Cerca**.

5. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md)
- [Procedura dettagliata: eseguire il debug di applicazioni multithread utilizzando la finestra thread](../debugger/how-to-use-the-threads-window.md)