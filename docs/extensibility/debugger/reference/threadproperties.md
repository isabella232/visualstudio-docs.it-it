---
title: THREADPROPERTIES | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
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

## <a name="members"></a>Members
 `dwFields`\
 Combinazione di flag dell'enumerazione [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , che descrive i campi di questa struttura validi.

 `dwThreadId`\
 ID del thread.

 `dwSuspendCount`\
 Conteggio di sospensione del thread.

 `dwThreadState`\
 Valore dell'enumerazione [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) che indica lo stato del thread operativo.

 `bstrPriority`\
 Stringa che specifica la priorità del thread. ad esempio, "sopra la normalità", "normale" o "tempo critico".

 `bstName`\
 Nome del thread.

 `bstrLocation`\
 Il percorso del thread, in genere il stack frame superiore, espresso in genere come nome del metodo in cui l'esecuzione è attualmente interrotta.

## <a name="remarks"></a>Osservazioni
 Questa struttura viene compilata tramite una chiamata al metodo [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Le informazioni restituite vengono in genere utilizzate per popolare la finestra **thread** .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
