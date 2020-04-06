---
title: Proprietà EncUnavailableReason . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737164"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Rappresenta i motivi per cui **Modifica e continuazione** non è disponibile.

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

## <a name="fields"></a>Campi
`ENCUN_NONE`\
Nessun motivo specifico per cui Modifica e continuazione non è disponibile.

`ENCUN_INTEROP`\
Modifica e continuazione non è disponibile durante una chiamata InterOp.

`ENCUN_SQLCLR`\
Modifica e continuazione non è disponibile durante una chiamata di procedura SQL che utilizza Common Language Runtime (CLR).

`ENCUN_MINIDUMP`\
Modifica e continuazione non è disponibile durante l'elaborazione di un minidump.

`ENCUN_EMBEDDED`\
Modifica e continuazione non è disponibile durante l'elaborazione del codice incorporato.

`ENCUN_ATTACH`\
Modifica e continuazione non è disponibile perché la sessione è stata collegata al debugger non avviata dal debugger.

`ENCUN_WIN64`\
Modifica e continuazione non è disponibile durante l'elaborazione di codice Windows a 64 bit.

## <a name="remarks"></a>Osservazioni
Questa enumerazione è per [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]uso interno solo da parte di . I metodi [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) e [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implementati da `E_NOTIMPL`un fornitore di porte personalizzato devono sempre restituire .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.idl

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
