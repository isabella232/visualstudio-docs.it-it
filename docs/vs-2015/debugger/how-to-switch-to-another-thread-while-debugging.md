---
title: 'Procedura: passare a un altro thread durante il debug | Microsoft Docs'
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
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176512"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Procedura: passare a un altro thread durante il debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si esegue il debug di un'applicazione multithreading, è possibile utilizzare diversi metodi per cambiare contesto passando dal thread utilizzato a un altro thread.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Per passare a un thread visualizzato nella finestra Thread  
  
- Fare doppio clic sul thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Per passare a un thread in una finestra di origine  
  
- Nella barra di navigazione a sinistra fare clic con il pulsante destro del mouse su un indicatore di thread, scegliere **passa a**, quindi fare clic sul nome del thread a cui si desidera passare. Nel menu di scelta rapida vengono visualizzati solo i thread presenti in quella determinata posizione.  
  
     Se non viene visualizzato alcun indicatore, fare clic con il pulsante destro del mouse nella finestra **thread** e verificare che **Mostra thread nell'origine** sia selezionato.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Per passare a un thread nella barra degli strumenti Posizione di debug  
  
1. Sulla barra degli strumenti **posizione di debug** fare clic sulla casella **thread** .  
  
2. Nell'elenco, fare clic sul thread al quale si desidera passare.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
