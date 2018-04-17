---
title: 'Procedura: passare a un altro Thread durante il debug | Documenti Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 064bd2ba65a3f6046475de45702d1093bbeab9d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Procedura: passare a un altro Thread durante il debug in Visual Studio
Quando si esegue il debug di un'applicazione multithreading, è possibile utilizzare uno dei diversi metodi per passare dal thread che sta utilizzando un altro thread.

> [!NOTE]
> Se si desidera controllare l'ordine in cui eseguono i thread, è necessario [bloccare e sbloccare i thread](../debugger/get-started-debugging-multithreaded-apps.md).

Quando si esaminano i thread nell'editor di codice e le diverse finestre di debug con multithreading, la freccia gialla indica che il thread corrente. Una freccia verde ricurva indica che un thread non correnti è il contesto di debug corrente.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Per passare a un thread visualizzato 
  
-   Nel **thread** o **espressioni di controllo parallelo** finestra, fare doppio clic sul thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Per passare a un thread in una finestra di origine  
  
-   Nella barra di navigazione a sinistra, fare doppio clic su un'icona marcatore thread ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker"), scegliere **passa a**, quindi fare clic sul nome del thread a cui si desidera passare . Nel menu di scelta rapida vengono visualizzati solo i thread presenti in quella determinata posizione.  
  
     Se nessun indicatore del thread viene visualizzato, fare clic del mouse il **thread** finestra e verificare che **Mostra thread nell'origine** è selezionata.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Per passare a un thread nella barra degli strumenti Posizione di debug  
  
1.  Nel **posizione di Debug** sulla barra degli strumenti, fare clic su di **Thread** elenco.  
  
2.  Nell'elenco, fare clic sul thread al quale si desidera passare.  
  
## <a name="see-also"></a>Vedere anche  
 [Il debug di applicazioni a thread multipli](../debugger/debug-multithreaded-applications-in-visual-studio.md)
