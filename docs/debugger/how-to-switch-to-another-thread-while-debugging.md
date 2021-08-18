---
title: Passare a un altro thread durante il debug
description: Esaminare metodi diversi per passare a un altro thread durante il debug di un'applicazione multithreading in Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7521218b895371127d4389ce2456a8c0f9274f6a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128104"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Procedura: Passare a un altro thread durante il debug in Visual Studio (C#, Visual Basic, C++)
Quando si esegue il debug di un'applicazione multithreading, è possibile usare uno dei diversi metodi per passare dal thread con cui si è lavorato a un altro thread.

> [!NOTE]
> Se si vuole controllare l'ordine di esecuzione dei thread, è necessario bloccare e [scosare i thread](../debugger/get-started-debugging-multithreaded-apps.md).

Quando si esaminano i thread nell'editor di codice e le diverse finestre di debug multithreading, la freccia gialla indica il thread corrente. Una freccia verde con una coda a forma di graffa indica che un thread non corrente ha il contesto del debugger corrente.

### <a name="to-switch-to-any-thread-that-appears"></a>Per passare a qualsiasi thread visualizzato

- Nella finestra **Thread** o **Controllo parallelo** fare doppio clic sul thread.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Per passare a un thread in una finestra di origine

- Nel riquadro sinistro fare clic con il pulsante destro del mouse sull'icona del marcatore di thread ![Marcatore](../debugger/media/dbg-thread-marker.png "ThreadMarker")thread , scegliere Passa a **e** quindi fare clic sul nome del thread a cui si vuole passare. Nel menu di scelta rapida vengono visualizzati solo i thread presenti in quella determinata posizione.

     Se non viene visualizzato alcun marcatore di thread, fare clic con il pulsante destro del mouse nella finestra **Thread** e verificare che **l'opzione Mostra thread nell'origine** sia selezionata.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Per passare a un thread nella barra degli strumenti Posizione di debug

1. Sulla barra **degli strumenti Percorso di** debug fare clic sull'elenco Thread . 

2. Nell'elenco, fare clic sul thread al quale si desidera passare.

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
