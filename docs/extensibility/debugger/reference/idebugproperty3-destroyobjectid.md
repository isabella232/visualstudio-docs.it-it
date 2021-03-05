---
description: Elimina l'ID univoco associato a questa proprietà, a indicare che il chiamante non è più in grado di identificare questa proprietà in modo univoco da tutte le altre proprietà.
title: IDebugProperty3::D estroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3712a12440f5d177f54544110bc8fa5d2e03ac
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166697"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Elimina l'ID univoco associato a questa proprietà, a indicare che il chiamante non è più in grado di identificare questa proprietà in modo univoco da tutte le altre proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Se il motore di debug non deve supportare ID univoci per una proprietà (poiché li tiene già in modo univoco internamente), può restituire semplicemente `E_NOTIMPL` per questo metodo.

 Gli ID univoci vengono creati con una chiamata al metodo [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) quando il chiamante vuole assicurarsi che questa proprietà sia identificata in modo univoco tra tutte le altre proprietà.

## <a name="see-also"></a>Vedi anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
