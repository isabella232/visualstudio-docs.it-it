---
title: Passare a un altro thread durante il debug
description: Esaminare metodi diversi per passare a un altro thread durante il debug di un'applicazione multithreading in Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 04/27/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8df37beafe7a6c8f88631568ea9eb36394c105a5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150717"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Procedura: passare a un altro thread durante il debug in Visual Studio (C#, Visual Basic, C++)
Quando si esegue il debug di un'applicazione multithreading, è possibile usare uno dei diversi metodi per passare dal thread che si sta utilizzando a un altro thread.

> [!NOTE]
> Se si desidera controllare l'ordine in cui vengono eseguiti i thread, è necessario [bloccare e sbloccare i thread](../debugger/get-started-debugging-multithreaded-apps.md).

Quando si esaminano i thread nell'editor di codice e le diverse finestre di debug multithreading, la freccia gialla indica il thread corrente. Una freccia verde con una coda riccia indica che un thread non corrente ha il contesto del debugger corrente.

### <a name="to-switch-to-any-thread-that-appears"></a>Per passare a un thread che viene visualizzato

- Nella finestra **thread** o espressione di **controllo in parallelo** fare doppio clic sul thread.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Per passare a un thread in una finestra di origine

- Nella barra di navigazione a sinistra fare clic con il pulsante destro del mouse sul ![marcatore del thread](../debugger/media/dbg-thread-marker.png "ThreadMarker")dell'icona del marcatore del thread, scegliere **passa a**, quindi fare clic sul nome del thread a cui si desidera passare. Nel menu di scelta rapida vengono visualizzati solo i thread presenti in quella determinata posizione.

     Se non viene visualizzato alcun marcatore di thread, fare clic con il pulsante destro del mouse nella finestra **thread** e verificare che l'opzione **Mostra thread nell'origine** sia selezionata.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Per passare a un thread nella barra degli strumenti Posizione di debug

1. Sulla barra degli strumenti **posizione di debug** fare clic sull'elenco **thread** .

2. Nell'elenco, fare clic sul thread al quale si desidera passare.

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
