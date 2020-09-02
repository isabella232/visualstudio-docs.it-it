---
title: Processi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153664"
---
# <a name="processes"></a>Processi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **processo**:  
  
- È un contenitore per un set di programmi. È strettamente analogo a un processo di Windows, che è un contenitore per un set di thread.  
  
- Può identificare se stesso in base al nome, all'identificatore o all'identificatore fisico.  
  
- Consente di enumerare tutti i programmi in esecuzione e i relativi thread.  
  
- Può descrivere se stesso, la porta in cui è in esecuzione e il computer che lo contiene.  
  
- Può creare uno o più programmi, terminare uno dei programmi creati o causare l'arresto di un programma.  
  
- È rappresentato da un'interfaccia [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , che viene creata all'avvio del processo. Un processo viene avviato da gestione debug sessione (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
  Il pacchetto di debug può alleghiare un motore di debug (DE) a un processo chiamando [Connetti](../../extensibility/debugger/reference/idebugprocess2-attach.md). Ciò significa che il DE si connette a tutti i programmi possibili in esecuzione nel processo che può gestire. Se, ad esempio, il Common Language Runtime DE si connette a un processo, viene collegato solo ai programmi che eseguono codice gestito.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Debug del pacchetto](../../extensibility/debugger/debug-package.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
