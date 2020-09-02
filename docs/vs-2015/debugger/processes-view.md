---
title: Visualizzazione processi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8b9c04d1cabd44418c70725ef331c9c4b5ec67e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580503"
---
# <a name="processes-view"></a>Visualizzazione processi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella visualizzazione processi viene visualizzato un albero di tutti i processi attivi nel sistema. Vengono visualizzati l'ID del processo e il nome del modulo. Utilizzare la visualizzazione processi se si desidera esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione. I processi sono identificati dai nomi dei moduli o sono designati come "processi di sistema".  
  
 Microsoft Windows supporta più processi. Ogni processo può avere uno o più thread e ogni thread può avere una o più finestre di primo livello associate. Ogni finestra di primo livello può essere proprietaria di una serie di finestre. Un simbolo + indica che un livello è compresso. La visualizzazione compressa è costituita da una riga per processo. Per espandere il livello, fare clic sul simbolo +.  
  
 Utilizzare la visualizzazione processi se si desidera esaminare un particolare processo di sistema, che in genere corrisponde a un programma in esecuzione. I processi sono identificati dai nomi dei moduli o sono designati come "processi di sistema". Per trovare un processo, comprimere l'albero ed eseguire una ricerca nell'elenco.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-open-the-processes-view"></a>Per aprire la visualizzazione processi  
  
1. Scegliere **processi**dal menu **Spy** .  
  
   ![Visualizzazione processi di Spy&#43;&#43; ](../debugger/media/spy-processes.png "_Processes di Spy + +")  
   Visualizzazione processi di Spy++  
  
   Nella figura precedente viene illustrata la visualizzazione processi con i nodi processo e thread espansi.  
  
### <a name="in-this-section"></a>Contenuto della sezione  
 [Ricerca di un processo nella visualizzazione processi](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Viene illustrato come trovare un processo specifico nella visualizzazione processi.  
  
 [Visualizzazione delle proprietà del processo](../debugger/how-to-display-process-properties.md)  
 Viene illustrato come visualizzare ulteriori informazioni su un messaggio.  
  
### <a name="related-sections"></a>Sezioni correlate  
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)  
 Illustra le visualizzazioni ad albero di Spy + + di Windows, i messaggi, i processi e i thread.  
  
 [Utilizzo di Spy++](../debugger/using-spy-increment.md)  
 Introduce lo strumento Spy + + e spiega come può essere usato.  
  
 [Finestra di dialogo Ricerca processi](../debugger/process-search-dialog-box.md)  
 Utilizzato per trovare il nodo per un processo specifico nella visualizzazione processi.  
  
 [Finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md)  
 Consente di visualizzare le proprietà di un processo selezionato nella visualizzazione processi.  
  
 [Riferimenti per Spy++](../debugger/spy-increment-reference.md)  
 Include sezioni che descrivono ogni menu e finestra di dialogo di Spy + +.
