---
title: 'Procedura: Impostare e rimuovere i flag dei thread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e63f081ff54a18bb4b5ca5c1cbdf947670f10a7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906725"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Procedura: Impostare e rimuovere i flag dei thread (C#, Visual Basic, C++)

È possibile contrassegnare un thread che si desidera prestare particolare attenzione mediante un'icona nella **thread**, **stack in parallelo** (visualizzazione thread), **espressioni di controllo parallela**e  **Thread GPU** windows. Questa icona può essere d'aiuto all'utente e ad altri per distinguere i thread con flag dagli altri thread.

Thread con flag ricevono inoltre un trattamento speciale nel **Thread** elenco le **posizione di Debug** sulla barra degli strumenti e le altre finestre di debug con multithreading. È possibile visualizzare tutti i thread o un solo thread con flag nel **Thread** elenco o in altre finestre.

### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread

- Nel **thread** oppure **espressioni di controllo parallela** finestra, trovare il thread si è interessati e fare clic sull'icona del flag per selezionare o deselezionare il flag.
- Nel **stack in parallelo** finestra, pulsante destro del mouse su un thread o un gruppo di thread e selezionare **Flag / \<thread >** oppure **Rimuovi flag / \<thread >**.

### <a name="to-unflag-all-threads"></a>Per rimuovere i flag di tutti thread

- Nella finestra **Thread** fare clic con il pulsante destro del mouse su un thread qualsiasi, quindi scegliere **Rimuovi flag di tutti i thread**.
- Nel **espressioni di controllo parallela** finestra, seleziona tutti i thread con flag, quindi fare doppio clic e selezionare **Rimuovi flag**.

### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag

- Scegliere il **Mostra solo con flag thread** pulsante in una delle finestre di debug con multithreading.

### <a name="to-flag-just-my-code"></a>Per contrassegnare Just My Code

1. Fare clic sull'icona del flag nella barra degli strumenti in cima alla finestra **Thread**.

2. Fare clic su **Contrassegna Just My Code** nell'elenco a discesa.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Per contrassegnare thread associati ai moduli selezionati

1. Fare clic sull'icona del flag nella barra degli strumenti della finestra **Thread**.

2. Fare clic su **Contrassegna selezione moduli personalizzata** nell'elenco a discesa.

3. Selezionare i moduli desiderati nella finestra di dialogo **Seleziona moduli**.

4. (Facoltativo) Digitare una stringa per cercare moduli specifici nella casella **Cerca**.

5. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md)
- [Procedura dettagliata: Debug di applicazioni multithreading con la finestra thread](../debugger/how-to-use-the-threads-window.md)