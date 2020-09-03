---
title: Eseguire il debug di unit test con Esplora test
description: Informazioni su come eseguire il debug di unit test con Esplora test in Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2def56c6a3860ce0476f448f87bdde25c7970807
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86393530"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Eseguire il debug e analizzare unit test con Esplora test

È possibile usare Esplora test per avviare una sessione di debug per i test. Esaminando con facilità il codice grazie al debugger di Visual Studio è possibile spostarsi in avanti e indietro tra gli unit test e i progetti da testare. Per avviare il debug:

1. Nell'editor di Visual Studio impostare un punto di interruzione in uno o più metodi di test di cui si vuole eseguire il debug.

    > [!NOTE]
    > Poiché i metodi di test possono essere eseguiti in qualsiasi ordine, impostare punti di interruzione in tutti i metodi di test di cui si vuole eseguire il debug.

::: moniker range="vs-2017"
2. In Esplora test selezionare i metodi di test e quindi scegliere **Esegui debug test selezionati** dal menu di scelta rapida.
::: moniker-end
::: moniker range=">=vs-2019"
2. In Esplora test selezionare i metodi di test e quindi scegliere **debug** dal menu di scelta rapida.

   ![Dettagli sull'esecuzione dei test](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Per altre informazioni sul debugger, vedere [Debug in Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Diagnosticare i problemi di prestazioni dei metodi di test

::: moniker range="vs-2017"
Per diagnosticare il motivo per cui un metodo di test richiede troppo tempo, selezionare il metodo in Esplora test e quindi scegliere **Esegui profilatura del test selezionato** dal menu di scelta rapida. Vedere [report sulla profilatura della strumentazione](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).
::: moniker-end

::: moniker range=">=vs-2019"
Per diagnosticare il motivo per cui un metodo di test richiede troppo tempo, selezionare il metodo in Esplora test e quindi scegliere **Profilo** dal menu di scelta rapida. Vedere [report sulla profilatura della strumentazione](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).
::: moniker-end

> [!NOTE]
> Questa funzionalità non è attualmente supportata per .NET Core.

## <a name="see-also"></a>Vedere anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
- [Domande frequenti su Esplora test](test-explorer-faq.md)
