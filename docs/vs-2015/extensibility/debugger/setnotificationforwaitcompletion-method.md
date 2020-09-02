---
title: Metodo SetNotificationForWaitCompletion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874e31c331f16e760e030f337dda715473b77af8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423400"
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta o cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametri  
 `enabled`  
  
 `true` per impostare il bit; `false` per annullare il bit.  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Osservazioni  
 Il debugger imposta questo bit per uscire da un corpo del metodo asincrono. Se `enabled` è `true` , questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Se `enabled` è `false` , questo metodo può essere chiamato sulle attività completate. In entrambi gli eventi deve essere usato solo per le attività di tipo Promise.  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
