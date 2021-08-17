---
description: Rimuove l'elenco di eccezioni impostate dall'IDE per una particolare architettura o linguaggio di runtime.
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e8a11b47421f95e4527095f0e696795e8f3785d4c95679faebd05563d59a3bb8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342258"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Rimuove l'elenco di eccezioni impostate dall'IDE per una particolare architettura o linguaggio di runtime.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>Parametri
`guidType`\
[in] GUID per il linguaggio o GUID per il motore di debug specifico di un'architettura di runtime.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le eccezioni rimosse da questo metodo sono state impostate da chiamate precedenti al [metodo SetException.](../../../extensibility/debugger/reference/idebugengine2-setexception.md)

 Per rimuovere un'eccezione specifica, chiamare il [metodo RemoveSetException.](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
