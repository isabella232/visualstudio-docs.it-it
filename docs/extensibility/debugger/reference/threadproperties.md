---
title: PROPRIETÀ THREAD Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713427"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Descrive le proprietà di un thread.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Membri
 `dwFields`\
 Combinazione di flag dall'enumerazione [THREADPROPERTY_FIELDS,](../../../extensibility/debugger/reference/threadproperty-fields.md) che descrive quali campi in questa struttura sono validi.

 `dwThreadId`\
 ID del thread.

 `dwSuspendCount`\
 Conteggio delle sospensioni del thread.

 `dwThreadState`\
 Valore dell'enumerazione [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) che indica lo stato del thread operativo.

 `bstrPriority`\
 Una stringa che specifica la priorità del thread; ad esempio, "Sopra il normale", "Normale" o "Critico tempo".

 `bstName`\
 Nome del thread.

 `bstrLocation`\
 Posizione del thread (in genere lo stack frame più in alto), in genere espressa come nome del metodo in cui l'esecuzione è attualmente interrotta.

## <a name="remarks"></a>Osservazioni
 Questa struttura viene compilata da una chiamata al [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodo. Le informazioni restituite vengono in genere utilizzate per popolare la finestra **Thread.**

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
