---
title: Proprietà IEEVisualizerDataProvider::SetObjectForVisualizer . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab63f1e74e0cd3ac64a4d7e7687a9136075b41a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718085"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Questo metodo modifica l'oggetto rappresentato dal visualizzatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parametri
`pNewObject`\
[in] Oggetto da impostare.

`error`\
[fuori] Se si è verificato un errore durante l'impostazione dell'oggetto, questa stringa contiene il messaggio di errore.

`pException`\
[fuori] Se si è verificato un errore, questo oggetto contiene le informazioni sull'eccezione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Spetta all'implementatore determinare come vengono restituite le informazioni sugli errori. Tuttavia, è possibile che alcuni chiamanti possano solo cercare se un oggetto eccezione è stato restituito per sapere che si è verificato un errore, pertanto questo metodo deve sempre restituire un oggetto eccezione se si è verificato un errore. La stringa di errore deve essere fornita anche nel caso in cui il chiamante desideri utilizzarla.

## <a name="see-also"></a>Vedere anche
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
