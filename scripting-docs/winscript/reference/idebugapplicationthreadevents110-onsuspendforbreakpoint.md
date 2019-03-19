---
title: IDebugApplicationThreadEvents110::OnSuspendForBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e6a663d6c1e504d8e10ea26d7d5b395b5ba8025
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153084"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Determina se il thread è completamente sospesa per un punto di interruzione e non ha ancora ripreso l'esecuzione normale.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md) viene implementata da PDM v11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non ha parametri.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md)