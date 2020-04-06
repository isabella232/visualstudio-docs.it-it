---
title: Metodo SetNotificationForWaitCompletion . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712870"
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
Imposta o cancella il bit di stato del TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Sintassi

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametri
 `enabled`

 `true`per impostare il bit; `false` per annullare l'impostazione del bit.

## <a name="exceptions"></a>Eccezioni

## <a name="remarks"></a>Osservazioni
 Il debugger imposta questo bit per facilitare l'uscita dal corpo di un metodo asincrono. Se `enabled` `true`è , questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Quando `enabled` `false`è , questo metodo può essere chiamato sulle attività completate. In entrambi i casi, deve essere utilizzato solo per le attività di tipo promessa.

## <a name="requirements"></a>Requisiti

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
