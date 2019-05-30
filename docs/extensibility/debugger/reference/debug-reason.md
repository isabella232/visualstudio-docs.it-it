---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0502ab10398d37bcafee5316ba7e7566dbab4e01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346162"
---
# <a name="debugreason"></a>DEBUG_REASON
Specifica il motivo per cui è stato avviato il processo per eseguire il debug.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Campi
`DEBUG_REASON_ERROR`\
Si è verificato un errore non specifico (usato come una condizione predefinita quando nessuno degli altri motivi adattamento).

`DEBUG_REASON_USER_LAUNCHED`\
Il processo è stato avviato su richiesta dell'utente.

`DEBUG_REASON_USER_ATTACHED`\
Il processo già in esecuzione è stato collegato dall'utente.

`DEBUG_REASON_AUTO_ATTACHED`\
Il processo è stato associato automaticamente al quando è stata avviata.

`DEBUG_REASON_CAUSALITY`\
Il processo è stato avviato a causa dell'errore una *Just-In-Time* evento di debug (JIT).

## <a name="remarks"></a>Note
Restituito dal [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
