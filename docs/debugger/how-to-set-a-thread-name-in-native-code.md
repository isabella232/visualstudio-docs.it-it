---
title: 'Procedura: Impostare il nome di un Thread in codice nativo | Microsoft Docs'
ms.custom: ''
ms.date: 12/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9226e009936d0a644a5a6fcfcaba57bc3af25d7d
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803098"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Procedura: Impostare il nome di un thread in codice nativo
La denominazione dei thread è possibile in tutte le edizioni di Visual Studio. Tale denominazione è utile per tenere traccia dei thread nella finestra **Thread**.

## <a name="set-a-thread-name"></a>Impostare il nome di un thread

Il `SetThreadName` funzione è utile per l'impostazione e la visualizzazione thread se il debugger è collegato al codice in esecuzione. A partire da Visual Studio 2017 versione 15.6, è possibile usare la [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) funzione per impostare e visualizzare i nomi dei thread.

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

## <a name="set-a-thread-name-using-setthreadname"></a>Impostare il nome di un thread usando SetThreadName

Per impostare il nome di un thread nel programma, è anche possibile usare il `SetThreadName` funzionare, come illustrato nell'esempio di codice seguente. Si noti che il nome del thread viene copiato nel thread in modo da poter rilasciare la memoria per il parametro `threadName` .  Questo metodo Usa un approccio basata sulle eccezioni che funziona solo se il debugger è collegato al momento che viene utilizzato il metodo basata sulle eccezioni. Il nome di un thread impostati tramite questo metodo non sarà disponibile in strumenti di analisi delle prestazioni o dump.

Esempio di codice seguente viene illustrato come utilizzare `SetThreadName`:

```C++
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