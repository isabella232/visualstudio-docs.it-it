---
title: Impossibile visualizzare il codice sorgente o Disassembly | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd21a38123894e7254bf4af6629528f8af4bf52d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529393"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Impossibile visualizzare il codice sorgente o il disassembly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Debugger non è possibile visualizzare il codice sorgente o Disassembly](https://docs.microsoft.com/visualstudio/debugger/debugger-cannot-display-source-code-or-disassembly).  
  
Il testo del messaggio di errore è il seguente:  
  
 Impossibile visualizzare il codice sorgente o disassembly relativo alla posizione corrente in cui si è interrotta l'esecuzione.  
  
 Questo messaggio di errore può essere visualizzato in alcune situazioni:  
  
-   È possibile che sia stato raggiunto un punto di interruzione in una posizione per la quale non esiste un codice sorgente, mentre si esegue il debug di un linguaggio che non supporta il disassembly. Aprire il **i punti di interruzione** finestra, individuare il punto di interruzione ed eliminarlo.  
  
-   Se si sta eseguendo il debug di script, è possibile che sia stato raggiunto un punto di interruzione mentre non esistevano thread nel programma. Scegliere **passaggio** oppure **continua** dal **Debug** menu per riprendere il debug.  
  
-   È possibile che per aspetti relativi alla sicurezza il debugger non sia stato in grado di leggere lo stack, il thread, il registro e altre informazioni sul contesto dal programma di cui si sta eseguendo il debug. Questa condizione si verifica più spesso se si esegue il debug di un'applicazione Web e non si dispone dell'autorizzazione corretta per accedere alla directory virtuale. Impostare la sicurezza anonima per la directory virtuale e riprovare.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md)  (Debug in Visual Studio)  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)



