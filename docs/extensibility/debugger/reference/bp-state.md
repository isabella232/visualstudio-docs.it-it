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
ms.openlocfilehash: 0d8ff002c7f17abe0f33900fb7f798405dde78ee755965bfe2d24713eaea33d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434451"
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
