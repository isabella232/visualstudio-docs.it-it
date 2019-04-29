---
title: Utilizzo in fase di esecuzione dei controlli senza la libreria Run-Time di C | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2d9d97b9ba8a93864ec9af6ff02df7b20bbb35e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929643"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Utilizzo dei controlli runtime senza la libreria di runtime del linguaggio C
Se si collega il programma senza la libreria di runtime C, Usa **/NODEFAULTLIB**e si desidera usare i controlli in fase di esecuzione, è necessario collegarlo con RunTmChk.

`_RTC_Initialize` consente di inizializzare il programma per i controlli runtime. Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario verificare che il programma sia compilato con i controlli degli errori di runtime prima di chiamare `_RTC_Initialize`, come illustrato di seguito:

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario definire anche una funzione chiamata `_CRT_RTC_INITW`. `_CRT_RTC_INITW` consente di installare la funzione definita dall'utente come funzione di segnalazione degli errori predefinita, come illustrato di seguito:

```cpp
// C version:
_RTC_error_fnW __cdecl _CRT_RTC_INITW(
        void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler.
    return &MyErrorFunc;
}

// C++ version:
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(
       void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler:
    return &MyErrorFunc;
}
```

Dopo aver installato la funzione di segnalazione degli errori predefinita, sarà possibile installare altre funzioni di segnalazione degli errori con `_RTC_SetErrorFuncW`. Per altre informazioni, vedere [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>Vedere anche
[Procedura: Usare i controlli di runtime nativi](../debugger/how-to-use-native-run-time-checks.md)
