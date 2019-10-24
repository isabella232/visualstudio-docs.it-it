---
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
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737836"
---
# <a name="debugger-services-running-out-of-memory"></a>Memoria insufficiente per i servizi del debugger
I servizi di debug hanno esaurito la memoria e hanno causato la chiusura della sessione di debug.

## <a name="to-investigate-this-error-on-windows"></a>Per esaminare questo errore in Windows
- È possibile controllare il grafico della memoria del processo nella finestra **strumenti di diagnostica** per verificare se l'applicazione di destinazione sta riscontrando un'enorme crescita di memoria. In tal caso, usare lo strumento **utilizzo memoria** per diagnosticare il problema sottostante, vedere [analizzare l'utilizzo della memoria](../profiling/memory-usage.md).

- Se l'applicazione di destinazione non sembra utilizzare una grande quantità di memoria, utilizzare la finestra di **Gestione attività** per estrarre l'utilizzo della memoria di Visual Studio (devenv. exe), il processo di lavoro (msvsmon. exe) o di vs code (vsdbg. exe/vsdbg-UI. exe) per determinare se si tratta di una problema del debugger. Se il processo che ha esaurito la memoria è devenv. exe, provare a ridurre il numero di estensioni di Visual Studio in esecuzione.

## <a name="see-also"></a>Vedere anche
- [Post di Blog: analizzare la CPU e la memoria durante il debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Informazioni sulla gestione della memoria](/windows/win32/memory/about-memory-management)
