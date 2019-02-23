---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea1bbf8fe96abbf1e7bd9a92396d0dcfa4306445
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717039"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Rappresenta i motivi che **modifica e continuazione** non è disponibile.

## <a name="syntax"></a>Sintassi

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

#### <a name="parameters"></a>Parametri
Motivo specifico ENCUN_NONE nessun motivo per cui modifica e continuazione non è disponibile.

ENCUN_INTEROP modifica e continuazione non è disponibile durante una chiamata di interoperabilità.

ENCUN_SQLCLR modifica e continuazione non è disponibile durante una chiamata di procedura SQL che usa Common Language Runtime (CLR).

ENCUN_MINIDUMP modifica e continuazione non è disponibile durante l'elaborazione di un minidump.

ENCUN_EMBEDDED modifica e continuazione non è disponibile durante l'elaborazione del codice incorporato.

ENCUN_ATTACH modifica e continuazione non è disponibile perché la sessione è stata collegata a, non è avviato da, il debugger.

ENCUN_WIN64 modifica e continuazione non è disponibile durante l'elaborazione di codice Windows a 64 bit.

## <a name="remarks"></a>Note
Questa enumerazione è per uso interno solo da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. Il [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) e [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) metodi come implementato da un fornitore di porte personalizzato devono sempre restituire `E_NOTIMPL`.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.idl

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
