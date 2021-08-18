---
description: Crea un oggetto dati primitivo, ad esempio un integer semplice.
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 372275ec5623b8bf52a682c1240e5dcb76d4f837
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088718"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crea un oggetto dati primitivo, ad esempio un integer semplice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametri
`ot`\
[in] Valore [dell'enumerazione OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) che rappresenta il tipo di primitiva da creare.

`ppObject`\
[out] Restituisce un [oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo per creare un oggetto che rappresenta un oggetto primitivo che è un parametro della funzione rappresentata [dall'interfaccia IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md) Ad esempio, se la stringa dell'espressione è "myString(5)", questo metodo verrà usato per creare un oggetto che rappresenta il numero intero 5.

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
