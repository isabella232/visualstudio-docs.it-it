---
title: Testare ed eseguire il debug di un visualizzatore | Microsoft Docs
description: Testare ed eseguire il debug di un visualizzatore eseguendolo da un driver di test (host di sviluppo del visualizzatore) o installando in Visual Studio e chiamandolo da una finestra del debugger.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa97453d08650b78a02eda873a01afe9e376caec
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298244"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Procedura: testare un visualizzatore ed eseguirne il debug
Dopo avere scritto un visualizzatore, è necessario testarlo ed eseguirne il debug.

Una possibile soluzione per testare un visualizzatore consiste nell'installarlo in Visual Studio e nel chiamarlo da un finestra del debugger. Vedere [Procedura: Installare un visualizzatore.](../debugger/how-to-install-a-visualizer.md) In questo caso, sarà necessario usare una seconda istanza di Visual Studio per collegare ed eseguire il debug del visualizzatore, in esecuzione nella prima istanza del debugger.

Una soluzione più semplice per il debug di un visualizzatore consiste nell'eseguire il visualizzatore da un driver di test. Utilizzando le API del visualizzatore è possibile creare con facilità un driver di questo tipo, che viene definito *host di sviluppo del visualizzatore*.

>[!NOTE]
> Attualmente, il driver di test è supportato solo quando si chiama il visualizzatore da un'.NET Framework applicazione.

### <a name="to-create-a-visualizer-development-host"></a>Per creare un host di sviluppo del visualizzatore

1. Nella classe del lato debugger includere un metodo statico che consenta di creare un oggetto <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> e di chiamare il relativo metodo di visualizzazione:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Come parametri per la costruzione dell'host vengono utilizzati l'oggetto dati che verrà mostrato nel visualizzatore (`objectToVisualize`) e il tipo della classe del lato debugger.

2. Aggiungere l'istruzione riportata di seguito per chiamare `TestShowVisualizer`. Se il visualizzatore è stato creato in una libreria di classi, sarà necessario creare un eseguibile per chiamare la libreria di classi e inserire questa istruzione nell'eseguibile:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Per un esempio più completo, vedere [Procedura dettagliata: Scrittura di un visualizzatore in C#.](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: scrittura di un visualizzatore in C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
