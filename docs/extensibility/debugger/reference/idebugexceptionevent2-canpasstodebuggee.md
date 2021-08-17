---
description: Determina se il motore di debug supporta o meno l'opzione per passare questa eccezione al programma di cui è in corso il debug alla ripresa dell'esecuzione.
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6741866b2b056792ea58d03bdd3abd6ed0f28d1d532ff2b5070b1f3cbe8af5c0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292585"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina se il motore di debug supporta o meno l'opzione per passare questa eccezione al programma di cui è in corso il debug alla ripresa dell'esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` (l'eccezione può essere passata al programma) o `S_FALSE` (l'eccezione non può essere passata).

## <a name="remarks"></a>Commenti
 De deve avere un'azione predefinita per il passaggio all'oggetto del debug. L'IDE può ricevere [l'evento IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e chiamare il [metodo Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) senza chiamare il `CanPassToDebuggee` metodo . Pertanto, de deve avere un caso predefinito per passare o meno l'eccezione.

## <a name="see-also"></a>Vedi anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
