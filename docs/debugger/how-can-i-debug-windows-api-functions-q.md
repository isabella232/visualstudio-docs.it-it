---
title: Eseguire il debug Windows funzioni API | Microsoft Docs
description: Informazioni su come eseguire il debug Windows funzione API con simboli NT caricati. Nel codice a 32 bit si usa la forma decorata del nome della funzione per impostare il punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0181b37f5977bc2a978e452358874b9a768221804825450fcf87b5eb7910461f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453958"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Come è possibile eseguire il debug di funzioni API Windows?
Per eseguire il debug di una funzione API Windows con NT Symbols caricato, effettuare le operazioni seguenti.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Per impostare un punto di interruzione su una funzione Windows API con NT Symbols caricato

- Nel punto [di interruzione](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)della funzione immettere il nome della funzione insieme al nome della DLL in cui risiede la funzione (vedere l'operatore [di contesto](../debugger/context-operator-cpp.md)). Nel codice a 32 bit, utilizzare la forma decorata del nome della funzione. Ad esempio, per impostare un punto di interruzione su **MessageBeep**, è necessario immettere quanto segue.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Per ottenere il nome decorato, vedere Visualizzazione [dei nomi decorati.](/previous-versions/5x49w699(v=vs.140))

     È possibile testare il nome decorato e visualizzarlo nel codice disassembly. Mentre è in pausa in corrispondenza della funzione nel debugger Visual Studio, fare clic con il pulsante destro del mouse sulla funzione nell'editor del codice o nella finestra dello stack di chiamate e scegliere **Vai a Disassembly.**

- Nel codice a 64 bit è possibile usare il nome non dichiarato.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
