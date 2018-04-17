---
title: 'Procedura: cercare un processo nella visualizzazione processi | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 621d1bd084a96a094ae1a6bc3823b3da26aa734c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Procedura: cercare un processo nella visualizzazione processi
È possibile cercare un processo specifico nella visualizzazione processi utilizzando la relativa stringa di ID o un modulo di processo come criterio di ricerca. È inoltre possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo verranno visualizzati gli attributi del processo selezionato nell'albero del processo.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Per cercare un processo nella visualizzazione processi  
  
1.  Disporre le finestre in modo che Spy + + e attivo [visualizzazione processi](../debugger/processes-view.md) finestra sono visibili.  
  
2.  Dal **ricerca** menu, scegliere **Trova processo**  
  
     Il [dialogo Ricerca processi](../debugger/process-search-dialog-box.md) apre.  
  
3.  Digitare l'ID del processo o un modulo come criterio di ricerca.  
  
4.  Deselezionare tutti i campi per cui non si desidera specificare i valori.  
  
    > [!TIP]
    >  Per trovare tutti i processi appartenenti a un modulo, cancellare il **processo** e digitare il nome del modulo nel **modulo** casella. Utilizzare quindi **Trova successivo** per continuare la ricerca dei processi.  
  
5.  Scegliere **backup** o **verso il basso** per la direzione iniziale della ricerca.  
  
6.  Fare clic su **OK**.  
  
 Se viene trovato un processo di corrispondenza, viene evidenziato nel **visualizzazione processo** finestra.