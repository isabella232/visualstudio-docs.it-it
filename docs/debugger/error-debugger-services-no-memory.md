---
description: I servizi di debug hanno esaurito la memoria e hanno causato la chiusura della sessione di debug.
title: Memoria insufficiente per i servizi del debugger | Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: fe8ce3949336c9fb323e6477e2aed05b7a5b6365d07f299a84b6203f9c00ba57
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343993"
---
# <a name="debugger-services-running-out-of-memory"></a>Memoria insufficiente per i servizi del debugger
I servizi di debug hanno esaurito la memoria e hanno causato la chiusura della sessione di debug.

## <a name="to-investigate-this-error-on-windows"></a>Per analizzare questo errore in Windows
- È possibile controllare il grafico della memoria del processo nella **finestra Strumenti** di diagnostica per verificare se l'applicazione di destinazione sta riscontrando un aumento notevole della memoria. In tal caso, usare lo **strumento Utilizzo memoria** per diagnosticare qual è il problema sottostante, vedere Analizzare [l'utilizzo della memoria.](../profiling/memory-usage.md)

- Se l'applicazione di destinazione non sembra utilizzare una grande quantità di memoria, usare la finestra **Gestione attività** per controllare l'utilizzo della memoria di Visual Studio (devenv.exe), del processo di lavoro (msvsmon.exe) o di VS Code (vsdbg.exe/vsdbg-ui.exe) per determinare se si tratta di un problema del debugger. Se la memoria del processo è insufficientedevenv.exe, provare a ridurre il numero di estensioni Visual Studio in esecuzione.

## <a name="see-also"></a>Vedi anche
- [Post di blog: Analizzare CPU e memoria durante il debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Informazioni sulla gestione della memoria](/windows/win32/memory/about-memory-management)
