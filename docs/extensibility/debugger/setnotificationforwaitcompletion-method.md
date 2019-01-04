---
title: Metodo SetNotificationForWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4b488bcfb37696f4e18c8f32741e8f3ef861aed8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986115"
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
Imposta o Cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in *mscorlib. dll*)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
### <a name="parameters"></a>Parametri  
 `enabled`  
  
 `true` Per impostare il bit; `false` per annullare il bit.  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
 Il debugger imposta questo bit consentono di uscire il corpo di un metodo async. Se `enabled` è `true`, questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Quando `enabled` è `false`, questo metodo può essere chiamato in attività completate. In entrambi i casi deve solo essere utilizzato per le attività basato su promise.  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)