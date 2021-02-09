---
title: Impostare un nome di thread in codice nativo | Microsoft Docs
description: Impostare un nome di thread in codice nativo durante il debug di app multithread in Visual Studio. La denominazione dei thread viene utilizzata per tenere traccia dei thread nella finestra thread.
ms.custom: SEO-VS-2020
ms.date: 12/17/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 024926123e8a9967947d11635558eb6ea06077cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921676"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Procedura: impostare il nome di un thread in codice nativo
La denominazione dei thread è possibile in tutte le edizioni di Visual Studio. La denominazione dei thread è utile per identificare i thread di interesse nella finestra **thread** durante il debug di un processo in esecuzione. Un thread con nome riconoscibile può essere utile anche quando si esegue il debug post-mortem tramite l'ispezione dei dump di arresto anomalo del sistema e quando si analizzano le acquisizioni delle prestazioni usando vari strumenti.

## <a name="ways-to-set-a-thread-name"></a>Modalità di impostazione di un nome di thread

Esistono due modi per impostare un nome di thread. Il primo è tramite la funzione [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) . Il secondo consiste nel generare una particolare eccezione mentre il debugger di Visual Studio è collegato al processo. Ogni approccio presenta vantaggi e avvertenze. L'uso di `SetThreadDescription` è supportato a partire da Windows 10, versione 1607 o Windows Server 2016.

Vale la pena notare che _entrambi_ gli approcci possono essere utilizzati insieme, se necessario, poiché i meccanismi con i quali funzionano sono indipendenti tra loro.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Impostare il nome di un thread utilizzando `SetThreadDescription`

Vantaggi:
* I nomi dei thread sono visibili durante il debug in Visual Studio, indipendentemente dal fatto che il debugger sia stato collegato al processo al momento in cui viene richiamato SetThreadDescription.
* I nomi dei thread sono visibili durante l'esecuzione del debug post-mortem tramite il caricamento di un dump di arresto anomalo in Visual Studio.
* I nomi dei thread sono visibili anche quando si usano altri strumenti, ad esempio il debugger [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) e [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) Performance Analyzer.

Avvertenze:
* I nomi dei thread sono visibili solo in Visual Studio 2017 versione 15,6 e versioni successive.
* Quando si esegue il debug post mortem di un file di dump di arresto anomalo, i nomi dei thread sono visibili solo se l'arresto anomalo è stato creato in Windows 10 versione 1607, Windows Server 2016 o versioni successive di Windows.

*Esempio:*

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Impostare un nome di thread generando un'eccezione

Un altro modo per impostare il nome di un thread nel programma consiste nel comunicare il nome del thread desiderato al debugger di Visual Studio generando un'eccezione appositamente configurata.

Vantaggi:
* Funziona in tutte le versioni di Visual Studio.

Avvertenze:
* Funziona solo se il debugger è collegato al momento in cui viene usato il metodo basato sull'eccezione.
* I nomi di thread impostati utilizzando questo metodo non saranno disponibili nei dump o negli strumenti di analisi delle prestazioni.

*Esempio:*

La `SetThreadName` funzione illustrata di seguito illustra questo approccio basato sulle eccezioni. Si noti che il nome del thread verrà copiato automaticamente nel thread, in modo che la memoria per il `threadName` parametro possa essere rilasciata dopo il `SetThreadName` completamento della chiamata.

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

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Procedura: impostare il nome di un thread in codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)
