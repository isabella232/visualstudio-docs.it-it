---
title: 'Procedura: Impostare il nome di un Thread in codice nativo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 37554c8ba72257ee78b219774425c7e8acb305a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156675"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Procedura: Impostare il nome di un thread in codice nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostare il nome di un thread nel programma, utilizzare la funzione `SetThreadName` come illustrato nel seguente esempio di codice. Si noti che il nome del thread viene copiato nel thread in modo da poter rilasciare la memoria per il parametro `threadName` .  
  
## <a name="example"></a>Esempio  
  
```cpp  
//  
// Usage: SetThreadName ((DWORD)-1, "MainThread");  
//  
#include <windows.h>  
const DWORD MS_VC_EXCEPTION = 0x406D1388;  
#pragma pack(push,8)  
typedef struct tagTHREADNAME_INFO  
{  
    DWORD dwType; // Must be 0x1000.  
    LPCSTR szName; // Pointer to name (in user addr space).  
    DWORD dwThreadID; // Thread ID (-1=caller thread).  
    DWORD dwFlags; // Reserved for future use, must be zero.  
 } THREADNAME_INFO;  
#pragma pack(pop)  
void SetThreadName(DWORD dwThreadID, const char* threadName) {  
    THREADNAME_INFO info;  
    info.dwType = 0x1000;  
    info.szName = threadName;  
    info.dwThreadID = dwThreadID;  
    info.dwFlags = 0;  
#pragma warning(push)  
#pragma warning(disable: 6320 6322)  
    __try{  
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);  
    }  
    __except (EXCEPTION_EXECUTE_HANDLER){  
    }  
#pragma warning(pop)  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Procedura: Impostare il nome di un thread in codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)
