---
description: Questo metodo ottiene l'oggetto rappresentato da questo visualizzatore.
title: IEEVisualizerDataProvider::GetObjectForVisualizer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer method
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa3bc464611858345a5d1013b2d4f2ce264a789c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103572"
---
# <a name="ieevisualizerdataprovidergetobjectforvisualizer"></a>IEEVisualizerDataProvider::GetObjectForVisualizer
Questo metodo ottiene l'oggetto rappresentato da questo visualizzatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametri
`ppObject`\
[out] Oggetto rappresentato da questo visualizzatore

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 `GetObjectForVisualizer` è consentito restituire una versione memorizzata nella cache dell'oggetto . Se il chiamante vuole assicurarsi che l'oggetto sia aggiornato, chiamerà [GetNewObjectForVisualizer.](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)

## <a name="see-also"></a>Vedi anche
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
