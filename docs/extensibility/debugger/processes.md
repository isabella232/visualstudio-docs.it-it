---
title: Processi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738242"
---
# <a name="processes"></a>Processi
Nell'architettura del debugger, un *processo*:

- È un contenitore per un set di programmi. È strettamente analogo a un processo di Windows, che è un contenitore per un set di thread.

- Può identificare se stesso in base al nome, all'identificatore o all'identificatore fisico.

- Consente di enumerare tutti i programmi in esecuzione e i relativi thread.

- Può descrivere se stesso, la porta in cui è in esecuzione e il computer che lo contiene.

- Può creare uno o più programmi, terminare uno dei programmi creati o causare l'arresto di un programma.

- È rappresentato da un'interfaccia [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , che viene creata all'avvio del processo. Un processo viene avviato da gestione debug sessione (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Il pacchetto di debug può alleghiare un motore di debug (DE) a un processo chiamando [Connetti](../../extensibility/debugger/reference/idebugprocess2-attach.md), il che significa che il de si connette a tutti i possibili programmi in esecuzione nel processo che è in grado di gestire. Se, ad esempio, il Common Language Runtime DE si connette a un processo, viene collegato solo ai programmi che eseguono codice gestito.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Debug del pacchetto](../../extensibility/debugger/debug-package.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
