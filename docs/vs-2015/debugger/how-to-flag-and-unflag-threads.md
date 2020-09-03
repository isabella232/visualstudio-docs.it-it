---
title: 'Procedura: contrassegnare e decontrassegnare i thread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6d6a49dd9b90172686a90d92e6b630dd70b5cf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189432"
---
# <a name="how-to-flag-and-unflag-threads"></a>Procedura: impostare e rimuovere i flag dei thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile contrassegnare un thread che si desidera prestare particolare attenzione contrassegnando l'icona con un'icona nelle finestre **thread**, **stack in parallelo**, espressione di controllo in **parallelo**e **thread GPU** . Questa icona può essere d'aiuto all'utente e ad altri per distinguere i thread con flag dagli altri thread.  
  
 I thread contrassegnati ricevono anche un trattamento speciale nell'elenco dei **thread** sulla barra degli strumenti **posizione di debug** . In questo elenco possono essere visualizzati tutti i thread o soltanto i thread con flag. Quando si contrassegna un thread, l'elenco dei **thread** passa automaticamente a visualizzare solo i thread contrassegnati, ma è possibile tornare indietro per visualizzare tutti i thread nel modo appropriato.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Per impostare o rimuovere un flag di un thread utilizzando la finestra Thread  
  
- Nella finestra **thread** trovare il thread a cui si è interessati e fare clic sull'icona del flag per selezionare o deselezionare il flag.  
  
### <a name="to-unflag-all-threads"></a>Per rimuovere i flag di tutti thread  
  
- Nella finestra **Thread** fare clic con il pulsante destro del mouse su un thread qualsiasi, quindi scegliere **Rimuovi flag di tutti i thread**.  
  
### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
- Scegliere il pulsante del flag nella finestra di debug.  
  
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
 [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md)
