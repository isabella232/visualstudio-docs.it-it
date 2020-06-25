---
title: Eseguire il debug di funzioni API Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 06/03/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4141cc1c1bee201435c63317c662181113dff70
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286403"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Come è possibile eseguire il debug di funzioni API Windows?
Per eseguire il debug di una funzione API Windows con NT Symbols caricato, effettuare le operazioni seguenti.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Per impostare un punto di interruzione su una funzione Windows API con NT Symbols caricato

- Nel punto di [interruzione della funzione](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)immettere il nome della funzione insieme al nome della dll in cui risiede la funzione (vedere l'operatore di [contesto](../debugger/context-operator-cpp.md)). Nel codice a 32 bit, utilizzare la forma decorata del nome della funzione. Ad esempio, per impostare un punto di interruzione su **MessageBeep**, è necessario immettere quanto segue.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Per ottenere il nome decorato, vedere [visualizzazione dei nomi decorati](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

     È possibile testare il nome decorato e visualizzarlo nel codice disassembly. Durante la sospensione della funzione nel debugger di Visual Studio, fare clic con il pulsante destro del mouse sulla funzione nell'editor del codice o nella finestra stack di chiamate e scegliere **Vai a disassembly**.

- Nel codice a 64 bit, è possibile usare il nome non decorato.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
