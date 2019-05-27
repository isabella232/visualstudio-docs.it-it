---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31bc89e248d609e8b828d4cc5b9ac41c8e15c70c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203701"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Questo metodo modifica l'oggetto che rappresenta il visualizzatore.

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
[out] Se si è verificato un errore durante l'impostazione dell'oggetto, questa stringa contiene il messaggio di errore.

`pException`\
[out] Se si è verificato un errore, questo oggetto contiene le informazioni sull'eccezione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 È responsabilità dell'implementatore per determinare le modalità di restituzione di informazioni sull'errore. Tuttavia, è possibile che alcuni chiamanti possano solo vedere se è stato restituito un oggetto eccezione conoscere presenti l'aspetto è verificato un errore, in modo che questo metodo deve sempre restituire un oggetto eccezione, se si è verificato un errore. La stringa di errore deve essere fornita anche nel caso in cui il chiamante desidera assicurarsi di usarla.

## <a name="see-also"></a>Vedere anche
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)