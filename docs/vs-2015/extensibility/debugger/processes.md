---
title: Processi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6428b6cb3a3bedac6b1deae35fd2cd7f501d70f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809883"
---
# <a name="processes"></a>Processi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **processo**:  
  
- È un contenitore per un set di programmi. È strettamente analoga a un processo di Windows, che è un contenitore per un set di thread.  
  
- Grado di identificarsi per nome, identificatore o identificatore fisico.  
  
- Possibile enumerare tutti i programmi in esecuzione (e i thread).  
  
- Possono descrivere se stesso, la porta in che è in esecuzione e i computer che lo contiene.  
  
- Può creare uno o più programmi, terminare tutti i programmi vengono creati o provocare un programma.  
  
- È rappresentato da un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaccia, che viene creato quando viene avviato il processo. Viene avviato un processo per la gestione a debug sessione (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
  Il pacchetto di debug può connettersi un motore di debug (DE) a un processo chiamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Ciò significa che la Germania collega tutti i programmi possibili in esecuzione nel processo che può gestire. Ad esempio, se common language runtime DE si collega a un processo, lo collega solo per i programmi che eseguono il codice gestito.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Eseguire il debug del pacchetto](../../extensibility/debugger/debug-package.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)

