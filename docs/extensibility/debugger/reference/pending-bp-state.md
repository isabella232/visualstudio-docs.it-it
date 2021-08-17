---
description: Specifica lo stato di un punto di interruzione in sospeso (un punto di interruzione che non è ancora stato associato).
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6079a227be831f44476a233849b735fadfc9e82564ea39af52637343caaa28e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448585"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Specifica lo stato di un punto di interruzione in sospeso (un punto di interruzione che non è ancora stato associato).

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Campi
 `PBPS_NONE`\
 Segnaposto per zero. Questo valore non viene mai restituito.

 `PBPS_DELETED`\
 Indica che il punto di interruzione in sospeso è stato eliminato.

 `PBPS_DISABLED`\
 Indica che il punto di interruzione in sospeso è disabilitato.

 `PBPS_ENABLED`\
 Indica che il punto di interruzione in sospeso è abilitato.

## <a name="remarks"></a>Commenti
 Usare come `state` membro [](../../../extensibility/debugger/reference/pending-bp-state-info.md) della struttura PENDING_BP_STATE_INFO.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
