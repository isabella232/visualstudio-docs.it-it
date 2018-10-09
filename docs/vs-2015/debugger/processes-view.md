---
title: Visualizzazione processi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c83b57ade3a78a4dcc926e34547ee566326e129
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526990"
---
# <a name="processes-view"></a>Visualizzazione processi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [visualizzazione processi](https://docs.microsoft.com/visualstudio/debugger/processes-view).  
  
La visualizzazione dei processi viene visualizzato un albero di tutti i processi attivi nel sistema. Vengono visualizzati il nome del modulo e l'ID processo. Se si vuole esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione, usare la visualizzazione dei processi. I processi sono identificati da nomi di modulo o vengono designati come "processi di sistema".  
  
 Microsoft Windows supporta più processi. Ogni processo può avere uno o più thread e ogni thread può avere uno o più associate finestre di primo livello. Ogni finestra di primo livello può disporre di una serie di windows. Un simbolo + indica che un livello è compressa. La visualizzazione compressa è costituito da una riga per ogni processo. Scegliere il simbolo + per espandere il livello.  
  
 Se si vuole esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione, usare la visualizzazione dei processi. I processi sono identificati da nomi di modulo o vengono designati come "processi di sistema". Per trovare un processo, comprimere l'albero e l'elenco di ricerca.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-open-the-processes-view"></a>Per aprire la visualizzazione dei processi  
  
1.  Dal **Spy** menu, scegliere **processi**.  
  
 ![Spy&#43; &#43; visualizzazione processi](../debugger/media/spy-processes.png "Spy + + _Processes")  
Visualizzazione processi di Spy++  
  
 La figura precedente mostra la visualizzazione dei processi con thread e processi nodi espansi.  
  
### <a name="in-this-section"></a>In questa sezione  
 [La ricerca di un processo nella visualizzazione processi](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Viene illustrato come trovare un processo specifico nella visualizzazione processi.  
  
 [Visualizzazione delle proprietà processo](../debugger/how-to-display-process-properties.md)  
 Viene illustrato come visualizzare altre informazioni su un messaggio.  
  
### <a name="related-sections"></a>Sezioni correlate  
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)  
 Illustra le visualizzazioni dell'albero Spy + + di windows, i messaggi, processi e thread.  
  
 [Uso di Spy++](../debugger/using-spy-increment.md)  
 Introduce lo strumento Spy + + e spiega come può essere usato.  
  
 [Finestra di dialogo Ricerca processi](../debugger/process-search-dialog-box.md)  
 Utilizzato per trovare il nodo per un determinato processo nella visualizzazione processi.  
  
 [Finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md)  
 Visualizza le proprietà di un processo selezionato nella visualizzazione processi.  
  
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)  
 Include varie sezioni che descrivono ogni Spy + + menu e la finestra di dialogo.


