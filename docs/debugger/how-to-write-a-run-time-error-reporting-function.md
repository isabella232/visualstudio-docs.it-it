---
title: Scrivere una funzione di segnalazione degli errori di | Microsoft Docs
description: Vedere esempi di scrittura di una funzione di segnalazione degli errori di run-time personalizzata in Visual Studio. Deve avere la stessa dichiarazione di _CrtDbgReportW e restituire il valore 1.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9f4131f5bea3f3c1a2c880c64302fd44ab5a3535
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146849"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>Procedura: Scrivere una funzione per la segnalazione degli errori di runtime (C++)
Una funzione personalizzata per la segnalazione degli errori di runtime deve avere la stessa dichiarazione di `_CrtDbgReportW` e deve restituire al debugger il valore 1.

Nell'esempio riportato di seguito viene illustrato come definire una funzione personalizzata per la segnalazione degli errori.

## <a name="example-1"></a>Esempio 1

```cpp
#include <stdio.h>
int errorhandler = 0;
void configureMyErrorFunc(int i)
{
    errorhandler = i;
}

int MyErrorFunc(int errorType, const wchar_t *filename,
                int linenumber, const wchar_t *moduleName,
                const wchar_t *format, ...)
{
    switch (errorhandler)
    {
    case 0:
    case 1:
        wprintf(L"Error type %d at %s line %d in %s",
                errorType, filename, linenumber, moduleName);
        break;
    case 2:
    case 3:
        fprintf(stderr, "Error type");
        break;
    }

    return 1;
}
```

## <a name="example-2"></a>Esempio 2
Nell'esempio che segue viene illustrata una funzione personalizzata più complessa. In questo esempio l'istruzione switch gestisce vari tipi di errore, definiti dal parametro `reportType` di `_CrtDbgReportW`. Poiché si sta sostituendo `_CrtDbgReportW`, non è possibile utilizzare `_CrtSetReportMode`. La funzione dovrà quindi gestire l'output. Nel primo argomento della variabile in questa funzione viene utilizzato un numero di errore di runtime. Per altre informazioni, vedere [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).

```cpp
#include <windows.h>
#include <stdarg.h>
#include <rtcapi.h>
#include <malloc.h>
#pragma runtime_checks("", off)
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,
                      const wchar_t *module, const wchar_t *format, ...)
{
    // Prevent re-entrance.
    static long running = 0;
    while (InterlockedExchange(&running, 1))
        Sleep(0);
    // Now, disable all RTC failures.
    int numErrors = _RTC_NumErrors();
    int *errors=(int*)_alloca(numErrors);
    for (int i = 0; i < numErrors; i++)
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);

    // First, get the rtc error number from the var-arg list.
    va_list vl;
    va_start(vl, format);
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);
    va_end(vl);

    wchar_t buf[512];
    const char *err = _RTC_GetErrDesc(rtc_errnum);
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",
        err,
        line,
        file ? file : L"Unknown",
        module ? module : L"Unknown");
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;
    // Now, restore the RTC errortypes.
    for(int i = 0; i < numErrors; i++)
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);
    running = 0;
    return res;
}
#pragma runtime_checks("", restore)
```

## <a name="example-3"></a>Esempio 3
Per installare questa funzione personalizzata al posto di `_RTC_SetErrorFuncW`, utilizzare `_CrtDbgReportW`. Per altre informazioni, vedere [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). Il valore restituito da `_RTC_SetErrorFuncW` è la funzione di segnalazione precedente, che può essere salvata e ripristinata in caso di necessità.

```cpp
#include <rtcapi.h>
int main()
{
    _RTC_error_fnW oldfunction, newfunc;
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);
    // Run some code.
    newfunc = _RTC_SetErrorFuncW(oldfunction);
    // newfunc == &MyErrorFunc;
    // Run some more code.
}
```

## <a name="see-also"></a>Vedi anche
[Personalizzazione dei Run-Time nativi](../debugger/native-run-time-checks-customization.md)
