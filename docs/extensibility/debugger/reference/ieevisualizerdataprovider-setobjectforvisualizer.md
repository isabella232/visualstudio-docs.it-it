---
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50d68b5cdb7399dc391ef90150f0b6a156783301
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890838"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Questo metodo modifica l'oggetto rappresentato dal visualizzatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parametri
`pNewObject`\
in Oggetto da impostare.

`error`\
out Se si è verificato un errore durante l'impostazione dell'oggetto, questa stringa contiene il messaggio di errore.

`pException`\
out Se si è verificato un errore, questo oggetto contiene le informazioni sull'eccezione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Spetta all'implementatore determinare il modo in cui vengono restituite le informazioni sugli errori. Tuttavia, è possibile che alcuni chiamanti possano controllare solo se è stato restituito un oggetto eccezione per sapere che si è verificato un errore, pertanto questo metodo deve restituire sempre un oggetto eccezione se si è verificato un errore. È necessario specificare anche la stringa di errore nel caso in cui il chiamante voglia utilizzarlo.

## <a name="see-also"></a>Vedi anche
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
