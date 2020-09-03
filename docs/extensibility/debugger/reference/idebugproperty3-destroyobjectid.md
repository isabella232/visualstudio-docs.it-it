---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721204"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Elimina l'ID univoco associato a questa proprietà, a indicare che il chiamante non è più in grado di identificare questa proprietà in modo univoco da tutte le altre proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Se il motore di debug non deve supportare ID univoci per una proprietà (poiché li tiene già in modo univoco internamente), può restituire semplicemente `E_NOTIMPL` per questo metodo.

 Gli ID univoci vengono creati con una chiamata al metodo [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) quando il chiamante vuole assicurarsi che questa proprietà sia identificata in modo univoco tra tutte le altre proprietà.

## <a name="see-also"></a>Vedere anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
