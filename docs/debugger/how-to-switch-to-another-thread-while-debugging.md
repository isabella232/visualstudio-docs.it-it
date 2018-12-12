---
title: Passare a un altro thread durante il debug
ms.custom: seodec18
ms.date: 04/27/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 45ace6f26f241ecdc39b88060fc4edc6c2e47d91
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057048"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Procedura: Passare a un altro Thread durante il debug in Visual Studio
Quando si esegue il debug di un'applicazione multithreading, è possibile utilizzare uno dei diversi metodi per passare dal thread che stava lavorando a un altro thread.

> [!NOTE]
> Se si desidera controllare l'ordine in cui vengono eseguiti i thread, è necessario [bloccare e sbloccare i thread](../debugger/get-started-debugging-multithreaded-apps.md).

Quando si esaminano i thread nell'editor del codice e finestre di debug con multithreading diversi, la freccia gialla indica che il thread corrente. Una freccia verde ricurva indica che un thread non corrente ha il contesto di debug corrente.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Passare a un thread visualizzato 
  
-   Nel **thread** oppure **espressioni di controllo parallela** finestra, fare doppio clic sul thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Per passare a un thread in una finestra di origine  
  
-   Nella barra di navigazione a sinistra, fare doppio clic su un'icona marcatore di thread ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker"), scegliere **passa a**e quindi fare clic sul nome del thread a cui si passa a . Nel menu di scelta rapida vengono visualizzati solo i thread presenti in quella determinata posizione.  
  
     Se viene visualizzato senza indicatori di thread, fare doppio clic nella **thread** finestra e verificare che **Mostra thread nell'origine** sia selezionata.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Per passare a un thread nella barra degli strumenti Posizione di debug  
  
1.  Nel **posizione di Debug** sulla barra degli strumenti, fare clic sui **Thread** elenco.  
  
2.  Nell'elenco, fare clic sul thread al quale si desidera passare.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
