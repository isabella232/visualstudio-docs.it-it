---
title: 'Procedura: cercare un Thread nella visualizzazione thread | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58e16d0edce411192f7b6e40bd0e5fedb32bfac5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880572"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Procedura: cercare un thread nella visualizzazione thread
È possibile cercare un thread specifico nella visualizzazione thread utilizzando la relativa stringa di ID o un modulo di thread come criterio di ricerca. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo mostrerà gli attributi del thread selezionato nell'albero del thread.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Per cercare un thread nella visualizzazione thread  
  
1. Disporre le finestre in modo tale Spy + + e un oggetto attivo [visualizzazione thread](../debugger/threads-view.md) finestra sono visibili.  
  
2. Dal **ricerca** menu, scegliere **trova Thread**.  
  
    Il [finestra di dialogo Ricerca Thread](../debugger/thread-search-dialog-box.md) apre.  
  
3. Digitare l'ID del thread o una stringa del modulo come criterio di ricerca.  
  
4. Deselezionare tutti i campi per cui non si desidera specificare i valori.  
  
   > [!TIP]
   >  Per trovare tutti i thread appartenenti a un modulo, cancellare il **Thread** casella di testo e il tipo di modulo assegnare un nome nel **modulo** casella. Quindi usare **Trova successivo** per continuare la ricerca per i thread.  
  
5. Scegli **iscrizione** oppure **verso il basso** per la direzione iniziale della ricerca.  
  
6. Fare clic su **OK**.  
  
   Se il thread corrispondente viene trovato, evidenziarlo nella finestra Visualizzazione thread.