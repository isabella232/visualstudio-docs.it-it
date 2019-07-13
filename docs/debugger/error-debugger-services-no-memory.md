---
title: Servizi di memoria insufficiente del debugger | Microsoft Docs
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
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854018"
---
# <a name="debugger-services-running-out-of-memory"></a>Servizi di memoria insufficiente del debugger
I servizi di debug ha esaurito la memoria e ha causato l'interruzione della sessione di debug.

## <a name="to-investigate-this-error-on-windows"></a>Per esaminare l'errore in Windows
- È possibile archiviare il grafico relativo alla memoria processo la **strumenti di diagnostica** finestra per vedere se l'applicazione di destinazione sta riscontrando notevole aumento delle dimensioni in memoria. In questo caso, usare il **utilizzo memoria** lo strumento diagnosi qual è il problema sottostante, vedere [analizzare l'utilizzo della memoria](../profiling/memory-usage.md).

- Se l'applicazione di destinazione non sembra essere utilizzare una grande quantità di memoria, usare il **Task Manager** finestra per estrarre l'utilizzo della memoria di Visual Studio (devenv.exe), il processo di lavoro (msvsmon.exe), o di Visual Studio Code (vsdbg.exe/vsdbg-ui.exe) per determinare se ciò costituisce un problema del debugger. Se il processo di memoria insufficiente è devenv.exe, provare a ridurre il numero di estensioni di Visual Studio in esecuzione.

## <a name="see-also"></a>Vedere anche
- [Post di blog: Analizzare CPU e memoria durante il debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Gestione della memoria](/windows/win32/memory/about-memory-management)
