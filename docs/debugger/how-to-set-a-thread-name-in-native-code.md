---
title: 'Procedura: impostare il nome di un Thread in codice nativo | Microsoft Docs'
ms.date: 12/17/2018
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c547dd00f7a5a31b949d22c13f305050355207c7
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227316"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Procedura: impostare il nome di un thread in codice nativo
La denominazione dei thread è possibile in tutte le edizioni di Visual Studio. Denominazione dei thread è utile per identificare i thread di interesse per il **thread** finestra durante il debug di un processo in esecuzione. Se i thread evidente denominato può anche essere utile quando si esegue il debug di finale tramite ispezione dei dump di arresto anomalo del sistema e quando l'analisi delle prestazioni acquisisce usando diversi strumenti.

## <a name="ways-to-set-a-thread-name"></a>Modi per impostare il nome di un thread

Esistono due modi per impostare il nome di un thread. Il primo è tramite il [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) (funzione). Il secondo è generando una particolare eccezione mentre il debugger di Visual Studio è collegato al processo. Ogni approccio presenta vantaggi e avvertenze.

Vale la pena notare che _entrambi_ gli approcci possono essere usati insieme, se si desidera, poiché i meccanismi che funzionano sono indipendenti tra loro.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Impostare il nome di un thread usando `SetThreadDescription`

I vantaggi sono:
* I nomi dei thread sono visibili quando il debug in Visual Studio, indipendentemente dal fatto se il debugger è stato collegato al processo nel momento in cui viene richiamato SetThreadDescription.
* I nomi dei thread sono visibili quando si esegue il debug post mortem, caricando un dump di arresto anomalo del sistema in Visual Studio.
* I nomi dei thread sono visibili anche quando si usano altri strumenti, ad esempio la [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) debugger e il [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) Analizzatore prestazioni.

Avvertenze:
* I nomi dei thread sono solo visibile in Visual Studio 2017 versione 15.6 e versioni successive.
* Quando i file di dump di debug di un arresto anomalo del sistema finale, sono visibili se l'arresto anomalo del sistema è stato creato in Windows 10 versione 1607, Windows Server 2016 o versioni successive di Windows solo i nomi dei thread.

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Impostare il nome di un thread generando un'eccezione

Un altro modo per impostare il nome di un thread nel programma consiste nel comunicare il nome del thread desiderata per il debugger di Visual Studio generando un'eccezione appositamente configurato.

I vantaggi sono:
* Funziona in tutte le versioni di Visual Studio.

Avvertenze:
* Funziona solo se il debugger è collegato al momento che viene utilizzato il metodo basata sulle eccezioni.
* I nomi dei thread impostati utilizzando questo metodo non sarà disponibile in strumenti di analisi delle prestazioni o dump.

*Esempio:*

Il `SetThreadName` funzione illustrato di seguito viene illustrato questo approccio basato sull'eccezione. Si noti che il nome del thread verrà copiato automaticamente al thread, in modo che la memoria per il `threadName` parametro può essere rilasciato dopo il `SetThreadName` chiamata è stata completata.

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
[Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)  
[Procedura: Impostare il nome di un thread in codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)
