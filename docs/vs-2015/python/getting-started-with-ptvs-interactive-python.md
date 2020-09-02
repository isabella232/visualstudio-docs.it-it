---
title: 'Introduzione a PTVS: Python interattivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550987"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>Introduzione a PTVS: Python interattivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I prompt o i cicli REPL (read-eval-print) interattivi sono uno strumento chiave per i linguaggi di programmazione produttivi,  che consentono di eseguire frammenti di codice per rilevare ed esaminare le API, sperimentare con il relativo uso e sviluppare in maniera interattiva codice di funzionamento da includere in progetti o programmi.  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Nella finestra Python Environments è visibile un elenco di tutti gli ambienti Python.  È possibile selezionarne uno per aprire una finestra interattiva o REPL.  Se è mai stato eseguito Python.exe in un prompt dei comandi si conosce già un REPL di Python.  Alla richiesta di REPL, si immette il codice e si preme Invio: in tal modo, verranno immediatamente visualizzati i risultati del codice.  Si tratta di un contesto di esecuzione Live che include tutto lo stato di tutte le esecuzioni, le assegnazioni di variabili e così via.  È possibile fare riferimento alle variabili che derivano da invii in seguito al prompt REPL.  È possibile scrivere più righe di codice ed eseguirle in una sola volta (ad esempio, una dichiarazione di metodo o più istruzioni).  
  
 REPL rappresenta un modo eccezionale per provare una nuova libreria.  È possibile importare la libreria, esaminare i sottopacchetti, le classi e le funzioni.  Python offre tutte queste informazioni tramite la relativa funzione `help()`.  Inoltre, Python Tools for Visual Studio (PTVS) offre suggerimenti e documentazione basati sui modelli di codice usati nell'editor, senza dover eseguire la libreria.  Quando si esegue il codice, PTVS usa informazioni dal runtime di Python per migliorare i suggerimenti di PTVS.  
  
 La Finestra interattiva è utile anche per lo sviluppo di codice iterativo o evolutivo, incluso il test del codice durante il relativo sviluppo.  È possibile selezionare una funzione in una finestra dell'editor, premere il pulsante del puntatore a destra e scegliere Invia a Interactive.  Questo comando copia la selezione nella finestra interattiva come input successivo e la esegue.  I risultati vengono visualizzati immediatamente.  Se è necessario apportare modifiche a input precedente, è possibile premere freccia su per ottenere il codice, modificarlo, quindi premere Ctrl + INVIO per eseguire il codice.  Premendo INVIO alla fine dell'input viene eseguito, ma premendo INVIO al centro del'input viene inserita un carattere di nuova riga.  
  
 È possibile aprire una finestra interattiva per ogni installazione di Python, senza alcun limite.  Nella parte superiore della finestra sono presenti pulsanti per cancellare la visualizzazione, reimpostare il contesto di esecuzione e così via.  La cronologia rimarrà intatta.  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione wiki](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [Video introduttivi e dettagliati su PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
