---
description: Specifica il motivo per cui è stato avviato il processo di debug.
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db5d6697f222015cc4f6dbedbc6258e00c9b285f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096252"
---
# <a name="debug_reason"></a>DEBUG_REASON
Specifica il motivo per cui è stato avviato il processo di debug.

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
Si è verificato un errore non specifico (usato come condizione predefinita quando nessuno degli altri motivi si adatta).

`DEBUG_REASON_USER_LAUNCHED`\
Il processo è stato avviato in corrispondenza della richiesta dell'utente.

`DEBUG_REASON_USER_ATTACHED`\
Il processo già in esecuzione è stato associato dall'utente.

`DEBUG_REASON_AUTO_ATTACHED`\
Il processo è stato associato automaticamente al momento dell'avvio.

`DEBUG_REASON_CAUSALITY`\
Il processo è stato avviato a causa di un evento di debug JIT ( *just-in-Time* ).

## <a name="remarks"></a>Commenti
Restituito dal metodo [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
