---
title: Metodo SetNotificationForWaitCompletion | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b1443bbbd49216330d1df9978052bf4d10f7157
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517103"
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [metodo SetNotificationForWaitCompletion](https://docs.microsoft.com/visualstudio/extensibility/debugger/setnotificationforwaitcompletion-method).  
  
Imposta o Cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametri  
 `enabled`  
  
 `true` Per impostare il bit; `false` per annullare il bit.  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
 Il debugger imposta questo bit consentono di uscire il corpo di un metodo async. Se `enabled` è `true`, questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Se `enabled` è `false`, questo metodo può essere chiamato su attività completate. In entrambi i casi deve solo essere utilizzato per le attività basato su promise.  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)

