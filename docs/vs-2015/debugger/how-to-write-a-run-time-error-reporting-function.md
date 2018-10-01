---
title: 'Procedura: scrivere una funzione di segnalazione degli errori di Run-Time | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94bbc0ff7d5ca06ca4ff7f84e1f2cb85c254b197
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529417"
---
# <a name="how-to-write-a-run-time-error-reporting-function"></a>Procedura: scrivere una funzione per la segnalazione degli errori di runtime
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: scrivere una funzione di segnalazione errori di Run-Time](https://docs.microsoft.com/visualstudio/debugger/how-to-write-a-run-time-error-reporting-function).  
  
Una funzione personalizzata per la segnalazione degli errori di runtime deve avere la stessa dichiarazione di `_CrtDbgReportW` e deve restituire al debugger il valore 1.  
  
 Nell'esempio riportato di seguito viene illustrato come definire una funzione personalizzata per la segnalazione degli errori.  
  
## <a name="example"></a>Esempio  
  
```  
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
  
## <a name="example"></a>Esempio  
 Nell'esempio che segue viene illustrata una funzione personalizzata più complessa. In questo esempio l'istruzione switch gestisce vari tipi di errore, definiti dal parametro `reportType` di `_CrtDbgReportW`. Poiché si sta sostituendo `_CrtDbgReportW`, non è possibile utilizzare `_CrtSetReportMode`. La funzione dovrà quindi gestire l'output. Nel primo argomento della variabile in questa funzione viene utilizzato un numero di errore di runtime. Per altre informazioni, vedere [RTC_SetErrorType](http://msdn.microsoft.com/library/f5f99be7-d357-4b11-b8f5-ddd3428f2b06).  
  
```  
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
  
## <a name="example"></a>Esempio  
 Per installare questa funzione personalizzata al posto di `_RTC_SetErrorFuncW`, utilizzare `_CrtDbgReportW`. Per altre informazioni, vedere [RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a). Il valore restituito da `_RTC_SetErrorFuncW` è la funzione di segnalazione precedente, che può essere salvata e ripristinata in caso di necessità.  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dei controlli runtime nativi](../debugger/native-run-time-checks-customization.md)





