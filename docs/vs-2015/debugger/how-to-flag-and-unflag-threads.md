---
title: 'Procedura: impostare e rimuovere i flag dei thread | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb6c6c3f9c333ef1613f2733a476e7843f7249b4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289133"
---
# <a name="how-to-flag-and-unflag-threads"></a>Procedura: impostare e rimuovere i flag dei thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile contrassegnare un thread che si desidera prestare particolare attenzione mediante un'icona nella **thread**, **stack in parallelo**, **espressioni di controllo parallela**, e **GPU Thread** windows. Questa icona può essere d'aiuto all'utente e ad altri per distinguere i thread con flag dagli altri thread.  
  
 Thread con flag ricevono inoltre un trattamento speciale nel **Thread** elenco le **posizione di Debug** sulla barra degli strumenti. In questo elenco possono essere visualizzati tutti i thread o soltanto i thread con flag. Quando si contrassegna un thread, il **Thread** elenco automaticamente cambia per mostrare solo thread con flag, ma è possibile tornare indietro per mostrare tutti i thread come appropriato.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Per impostare o rimuovere un flag di un thread utilizzando la finestra Thread  
  
-   Nel **thread** finestra, trovare il thread si è interessati e fare clic sull'icona del flag per selezionare o deselezionare il flag.  
  
### <a name="to-unflag-all-threads"></a>Per rimuovere i flag di tutti thread  
  
-   Nel **thread** finestra, fare doppio clic su uno o più thread e quindi fare clic su **Rimuovi flag di tutti i thread**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante del flag nella finestra di debug.  
  
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
 [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md)



