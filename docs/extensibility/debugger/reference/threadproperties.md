---
description: Descrive le proprietà di un thread.
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42b5811169a7138cda0d292793bb1ccbaca7316c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634747"
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
 Combinazione di flag [dell'enumerazione THREADPROPERTY_FIELDS,](../../../extensibility/debugger/reference/threadproperty-fields.md) che descrive i campi di questa struttura validi.

 `dwThreadId`\
 ID thread.

 `dwSuspendCount`\
 Conteggio di sospensione del thread.

 `dwThreadState`\
 Valore [dell'enumerazione THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) che indica lo stato del thread operativo.

 `bstrPriority`\
 Stringa che specifica la priorità del thread. ad esempio "Above Normal", "Normal" o "Time Critical".

 `bstName`\
 Nome del thread.

 `bstrLocation`\
 Posizione del thread (in genere la posizione stack frame), in genere espressa come nome del metodo in cui l'esecuzione è attualmente interrotta.

## <a name="remarks"></a>Commenti
 Questa struttura viene compilata da una chiamata al [metodo GetThreadProperties.](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) Le informazioni restituite vengono in genere usate per popolare la **finestra** Thread.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
