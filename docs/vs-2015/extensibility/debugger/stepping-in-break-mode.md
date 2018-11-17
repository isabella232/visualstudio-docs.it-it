---
title: Esecuzione di istruzioni in modalità di interruzione | Microsoft Docs
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
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4400bcbecce322185ec514e6d05ac9a37e27fdde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749092"
---
# <a name="stepping-in-break-mode"></a>Esecuzione di istruzioni in modalità di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve esaminare il codice:  
  
## <a name="stepping-process"></a>Processo di debug passo a passo  
  
1.  Chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) con [STEPKIND](../../extensibility/debugger/reference/stepkind.md) e [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argomenti per eseguire un passaggio.  
  
2.  Quando viene completato il passaggio, inviare un' [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) come un evento di arresto.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)

