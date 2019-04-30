---
title: 'Procedura: Cercare un Thread nella visualizzazione thread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5974bc962faf439af8de5d50bf51bad3d824647
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439080"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Procedura: Cercare un thread nella visualizzazione thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile cercare un thread specifico nella visualizzazione thread utilizzando la relativa stringa di ID o un modulo di thread come criterio di ricerca. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo mostrerà gli attributi del thread selezionato nell'albero del thread.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Per cercare un thread nella visualizzazione thread  
  
1. Disporre le finestre in modo tale Spy + + e un oggetto attivo [visualizzazione thread](../debugger/threads-view.md) finestra sono visibili.  
  
2. Dal **ricerca** menu, scegliere **trova Thread**.  
  
    Il [finestra di dialogo Ricerca Thread](../debugger/thread-search-dialog-box.md) apre.  
  
3. Digitare l'ID del thread o una stringa del modulo come criterio di ricerca.  
  
4. Deselezionare tutti i campi per cui non si desidera specificare i valori.  
  
   > [!TIP]
   > Per trovare tutti i thread appartenenti a un modulo, cancellare il **Thread** casella di testo e il tipo di modulo assegnare un nome nel **modulo** casella. Quindi usare **Trova successivo** per continuare la ricerca per i thread.  
  
5. Scegli **iscrizione** oppure **verso il basso** per la direzione iniziale della ricerca.  
  
6. Fare clic su **OK**.  
  
   Se il thread corrispondente viene trovato, evidenziarlo nella finestra Visualizzazione thread.
