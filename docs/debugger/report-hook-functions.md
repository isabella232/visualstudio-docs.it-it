---
title: Funzioni hook per la creazione di report | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7de5ae8611a3577902d5a6a893d7971ac40cc88b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="report-hook-functions"></a>Funzioni hook per la creazione di rapporti
Una funzione hook di report, installata mediante [CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), viene chiamato ogni volta [CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un report di debug. È possibile utilizzare tale funzione, ad esempio, per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni. Una funzione hook per la creazione di report deve avere un prototipo analogo al seguente:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Il puntatore passato a **CrtSetReportHook** è di tipo **CRT_REPORT_HOOK**, come definito in CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, il *nRptType* argomento contiene la categoria del report (**CRT_WARN**, **CRT_ERROR**, o **_CRT Assert**), *szMsg* contiene un puntatore a una stringa di messaggio di report completa, e *retVal* specifica se `_CrtDbgReport` deve continuare l'esecuzione normale Dopo aver generato il report o avviare il debugger. (A *retVal* valore zero l'esecuzione continua, il valore 1 viene avviato il debugger.)  
  
 Se la funzione hook gestisce il messaggio in questione completamente, in modo che sia necessario alcun report ulteriore, deve restituire **TRUE**. Se restituisce **FALSE**, `_CrtDbgReport` visualizzerà il messaggio normalmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di funzioni Hook di debug](../debugger/debug-hook-function-writing.md)   
 [Esempio crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)