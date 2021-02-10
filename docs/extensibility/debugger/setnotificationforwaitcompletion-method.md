---
title: Metodo SetNotificationForWaitCompletion | Microsoft Docs
description: Informazioni sul modo in cui il debugger usa un bit di stato per uscire da un corpo del metodo asincrono per le attività di tipo Promise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2418e958c027fea7fd39c93b0d5abbd95d64435b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960793"
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
Imposta o cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Sintassi

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametri
 `enabled`

 `true` per impostare il bit; `false` per annullare il bit.

## <a name="exceptions"></a>Eccezioni

## <a name="remarks"></a>Osservazioni
 Il debugger imposta questo bit per uscire da un corpo del metodo asincrono. Se `enabled` è `true` , questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Quando `enabled` è `false` , questo metodo può essere chiamato sulle attività completate. In entrambi gli eventi deve essere usato solo per le attività di tipo Promise.

## <a name="requirements"></a>Requisiti

## <a name="see-also"></a>Vedi anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
