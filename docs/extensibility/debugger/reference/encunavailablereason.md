---
description: Rappresenta i motivi per cui Modifica e continuazione non è disponibile.
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a47c29f07a590667a22ed123ba660202b4de9c449e606a8d921dd02eb0b7f52
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434399"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Rappresenta i motivi per cui **Modifica e** continuazione non è disponibile.

## <a name="syntax"></a>Sintassi

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
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
Modifica e continuazione non è disponibile durante una SQL di routine che usa Common Language Runtime (CLR).

`ENCUN_MINIDUMP`\
Modifica e continuazione non è disponibile durante l'elaborazione di un minidump.

`ENCUN_EMBEDDED`\
Modifica e continuazione non è disponibile durante l'elaborazione del codice incorporato.

`ENCUN_ATTACH`\
Modifica e continuazione non è disponibile perché la sessione è stata collegata, non avviata dal debugger.

`ENCUN_WIN64`\
Modifica e continuazione non è disponibile durante l'elaborazione del codice Windows a 64 bit.

## <a name="remarks"></a>Commenti
Questa enumerazione è per uso interno solo da parte di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . I [metodi GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) e [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implementati da un fornitore di porte personalizzato devono sempre restituire `E_NOTIMPL` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.idl

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
