---
title: PROPRIETÀ THREADSTATE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b291cc1668b2b867729da11d4c561f74567f257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713330"
---
# <a name="threadstate"></a>THREADSTATE
Specifica lo stato del thread.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Campi
 `THREADSTATE_RUNNING`\
 Indica che il thread è in esecuzione.

 `THREADSTATE_STOPPED`\
 Indica che il thread è stato arrestato a causa di un punto di interruzione.

 `THREADSTATE_FRESH`\
 Indica che il thread è stato creato, ma non è ancora in esecuzione codice.

 `THREADSTATE_DEAD`\
 Indica che il thread è morto.

 `THREADSTATE_FROZEN`\
 Indica che il thread è bloccato (non è possibile eseguire alcuna esecuzione).

## <a name="remarks"></a>Osservazioni
 Utilizzato per `dwThreadState` il campo della struttura [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
