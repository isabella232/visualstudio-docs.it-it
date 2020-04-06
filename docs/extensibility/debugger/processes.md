---
title: Processi Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738242"
---
# <a name="processes"></a>Processi
Nell'architettura del debugger, un *processo*:

- È un contenitore per un insieme di programmi. È strettamente analogo a un processo di Windows, che è un contenitore per un set di thread.

- Può identificarsi in base al nome, all'identificatore o all'identificatore fisico.

- Può enumerare tutti i programmi in esecuzione (e i relativi thread).

- Può descrivere se stesso, la porta in cui è in esecuzione e la macchina che la contiene.

- Può creare uno o più programmi, terminare uno qualsiasi dei programmi creati o causare l'arresto di un programma.

- È rappresentato da un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaccia, che viene creato quando viene avviato il processo. Un processo viene avviato dal gestore di sessione di debug (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Il pacchetto di debug può collegare un motore di debug (DE) a un processo chiamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), il che significa che il DE si connette a tutti i possibili programmi in esecuzione nel processo che è in grado di gestire. Ad esempio, se common language runtime DE si connette a un processo, si connette solo ai programmi che eseguono codice gestito.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Discussioni](../../extensibility/debugger/threads.md)
- [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md)
- [Pacchetto di debug](../../extensibility/debugger/debug-package.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
