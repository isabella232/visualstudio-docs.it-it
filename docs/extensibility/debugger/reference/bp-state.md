---
description: Specifica l'esistenza di un punto di interruzione associato e specifica anche se è abilitato.
title: BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d4136444a1d48a5ba70a9ed138897a008bbc036
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635211"
---
# <a name="bp_state"></a>BP_STATE
Specifica l'esistenza di un punto di interruzione associato e specifica anche se è abilitato.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Campi
`BPS_NONE`\
Specifica che non esiste alcun punto di interruzione.

`BPS_DELETED`\
Specifica che il punto di interruzione è stato eliminato.

`BPS_DISABLED`\
Specifica che il punto di interruzione è disabilitato.

`BPS_ENABLED`\
Specifica che il punto di interruzione è abilitato.

## <a name="remarks"></a>Commenti
Restituito dal [metodo GetState.](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
