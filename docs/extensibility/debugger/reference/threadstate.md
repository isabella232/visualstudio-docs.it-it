---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50f487b3d44fc1b871b00348ec28693b36c49685
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316135"
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
 Indica che il thread è inattivo.

 `THREADSTATE_FROZEN`\
 Indica che il thread è bloccato (Nessuna esecuzione può essere eseguita).

## <a name="remarks"></a>Note
 Utilizzato per il `dwThreadState` campo le [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struttura.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)