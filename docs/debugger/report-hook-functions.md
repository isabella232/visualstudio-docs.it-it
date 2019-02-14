---
title: Funzioni Hook di report | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18485d94aaedcb1f41c0ed747dc6af0be7f7e276
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952873"
---
# <a name="report-hook-functions"></a>Funzioni hook per la creazione di rapporti
Una funzione hook per la creazione di report, installata mediante [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), viene chiamata ogni volta che [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un report di debug. È possibile utilizzare tale funzione, ad esempio, per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni. Una funzione hook per la creazione di report deve avere un prototipo analogo al seguente:  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Il puntatore passato a **CrtSetReportHook** JE typu **CRT_REPORT_HOOK**, come definito in CRTDBG. H:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, l'argomento *nRptType* contiene la categoria del report (**_CRT_WARN**, **_CRT_ERROR** o **_CRT_ASSERT**), *szMsg* contiene un puntatore a una stringa di messaggio di report completa e *retVal* specifica se `_CrtDbgReport` debba continuare la normale esecuzione dopo la generazione del report o avviare invece il debugger (se *retVal* ha valore zero l'esecuzione continua, se ha valore 1 viene avviato il debugger).  
  
 Se la funzione hook gestisce il messaggio in questione completamente, in modo che non sia necessario alcun report ulteriore, deve restituire **TRUE**. Se restituisce **FALSE**, `_CrtDbgReport` visualizzerà il messaggio normalmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 Sample](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
