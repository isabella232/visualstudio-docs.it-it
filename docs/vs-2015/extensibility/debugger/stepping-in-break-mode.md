---
title: Esecuzione in modalità di interruzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423361"
---
# <a name="stepping-in-break-mode"></a>Esecuzione di istruzioni in modalità di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritto il processo che si verifica quando il debugger è in modalità di interruzione ed è necessario eseguire il codice un'istruzione alla volta:  
  
## <a name="stepping-process"></a>Esecuzione di un processo  
  
1. Chiamare [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con gli argomenti [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) per eseguire un passaggio.  
  
2. Al termine del passaggio, inviare un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) come evento di arresto.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
