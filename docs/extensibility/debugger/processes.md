---
title: Processi | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un processo nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6bc1ab72f9771ea8557b3f6688f2253744e322f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065176"
---
# <a name="processes"></a>Processi
Nell'architettura del debugger, un *processo*:

- Contenitore per un set di programmi. È molto simile a un processo Windows, che è un contenitore per un set di thread.

- Può identificarsi in base al nome, all'identificatore o all'identificatore fisico.

- Può enumerare tutti i programmi in esecuzione (e i relativi thread).

- Può descrivere se stesso, la porta in cui è in esecuzione e il computer che la contiene.

- Può creare uno o più programmi, terminare uno qualsiasi dei programmi creati o causare l'arresto di un programma.

- È rappresentato da [un'interfaccia IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) che viene creata all'avvio del processo. Un processo viene avviato da Gestione debug sessione (SDM) o [LaunchSuspended.](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

  Il pacchetto di debug può collegare un motore di debug (DE) a un processo chiamando [Attach,](../../extensibility/debugger/reference/idebugprocess2-attach.md)il che significa che de si connette a tutti i possibili programmi in esecuzione nel processo che può gestire. Ad esempio, se Common Language Runtime DE si connette a un processo, si collega solo ai programmi che eseguono codice gestito.

## <a name="see-also"></a>Vedi anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Thread](../../extensibility/debugger/threads.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Pacchetto di debug](../../extensibility/debugger/debug-package.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
