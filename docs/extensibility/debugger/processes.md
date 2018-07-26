---
title: Processi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c07a9cb6c16f09f2f55b543087e25d85bc300c0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251777"
---
# <a name="processes"></a>Processi
Nell'architettura di debugger, un *processo*:  
  
-   È un contenitore per un set di programmi. È strettamente analoga a un processo di Windows, che è un contenitore per un set di thread.  
  
-   Grado di identificarsi per nome, identificatore o identificatore fisico.  
  
-   Possibile enumerare tutti i programmi in esecuzione (e i thread).  
  
-   Possono descrivere se stesso, la porta in che è in esecuzione e i computer che lo contiene.  
  
-   Può creare uno o più programmi, terminare tutti i programmi vengono creati o provocare un programma.  
  
-   È rappresentato da un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaccia, che viene creato quando viene avviato il processo. Viene avviato un processo per la gestione a debug sessione (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Il pacchetto di debug può connettersi un motore di debug (DE) a un processo chiamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), il che significa che la Germania collega tutti i programmi possibili in esecuzione nel processo che può gestire. Ad esempio, se common language runtime DE si collega a un processo, lo collega solo per i programmi che eseguono il codice gestito.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Eseguire il debug del pacchetto](../../extensibility/debugger/debug-package.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)