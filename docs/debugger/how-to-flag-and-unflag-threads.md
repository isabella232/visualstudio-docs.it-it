---
title: 'Procedura: impostare e rimuovere i flag dei thread | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d26c87867e071b7dafce80d95e4bc46cb88bb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891375"
---
# <a name="how-to-flag-and-unflag-threads"></a>Procedura: impostare e rimuovere i flag dei thread
È possibile contrassegnare un thread che si desidera prestare particolare attenzione mediante un'icona nella **thread**, **stack in parallelo** (visualizzazione thread), **espressioni di controllo parallela**e  **Thread GPU** windows. Questa icona può essere d'aiuto all'utente e ad altri per distinguere i thread con flag dagli altri thread.  
  
Thread con flag ricevono inoltre un trattamento speciale nel **Thread** elenco le **posizione di Debug** sulla barra degli strumenti e le altre finestre di debug con multithreading. È possibile visualizzare tutti i thread o un solo thread con flag nel **Thread** elenco o in altre finestre.
  
### <a name="to-flag-or-unflag-a-thread"></a>Per aggiungere o rimuovere flag che contrassegnano un thread 
  
- Nel **thread** oppure **espressioni di controllo parallela** finestra, trovare il thread si è interessati e fare clic sull'icona del flag per selezionare o deselezionare il flag. 
- Nel **stack in parallelo** finestra, pulsante destro del mouse su un thread o un gruppo di thread e selezionare **Flag / <thread>**  oppure **Rimuovi flag / <thread>** .
  
### <a name="to-unflag-all-threads"></a>Per rimuovere i flag di tutti thread  
  
-   Nel **thread** finestra, fare doppio clic su uno o più thread e quindi fare clic su **Rimuovi flag di tutti i thread**.
-   Nel **espressioni di controllo parallela** finestra, seleziona tutti i thread con flag, quindi fare doppio clic e selezionare **Rimuovi flag**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il **Mostra solo con flag thread** pulsante in una delle finestre di debug con multithreading.  
  
### <a name="to-flag-just-my-code"></a>Per contrassegnare Just My Code  
  
1.  Sulla barra degli strumenti in cima il **thread** finestra, fare clic sull'icona del flag.  
  
2.  Nell'elenco a discesa elenco, fare clic su **Contrassegna Just My Code**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Per contrassegnare thread associati ai moduli selezionati  
  
1.  Nella barra degli strumenti di **thread** finestra, fare clic sull'icona del flag.  
  
2.  Nell'elenco a discesa elenco, fare clic su **Contrassegna selezione moduli personalizzata**.  
  
3.  Nel **Seleziona moduli** finestra di dialogo, selezionare i moduli desiderati.  
  
4.  (Facoltativo) Nel **ricerca** , digitare una stringa da cercare moduli specifici.  
  
5.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Procedura dettagliata: Debug di applicazioni multithreading con la finestra thread](../debugger/how-to-use-the-threads-window.md)