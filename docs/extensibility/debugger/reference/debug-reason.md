---
description: Specifica il motivo per cui il processo è stato avviato per il debug.
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 493328f0dbad03030c3f817177a5adb4dc213bc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160283"
---
# <a name="debug_reason"></a>DEBUG_REASON
Specifica il motivo per cui il processo è stato avviato per il debug.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Campi
`DEBUG_REASON_ERROR`\
Si è verificato un errore non specifico (viene usato come condizione predefinita quando nessuno degli altri motivi è adatto).

`DEBUG_REASON_USER_LAUNCHED`\
Il processo è stato avviato su richiesta dell'utente.

`DEBUG_REASON_USER_ATTACHED`\
Il processo già in esecuzione è stato collegato dall'utente.

`DEBUG_REASON_AUTO_ATTACHED`\
Il processo è stato collegato automaticamente a quando è stato avviato.

`DEBUG_REASON_CAUSALITY`\
Il processo è stato avviato a causa di un evento di debug JIT *(Just-In-Time).*

## <a name="remarks"></a>Commenti
Restituito dal [metodo GetDebugReason.](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
