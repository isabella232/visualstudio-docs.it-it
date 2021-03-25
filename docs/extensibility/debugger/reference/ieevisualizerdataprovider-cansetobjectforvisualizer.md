---
description: Questo metodo determina se il visualizzatore può avere l'oggetto dati che rappresenta aggiornato.
title: 'IEEVisualizerDataProvider:: CanSetObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81d958bb7cb931f485f8efa807dc9d322bab1fa4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058183"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
Questo metodo determina se il visualizzatore può avere l'oggetto dati che rappresenta aggiornato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanSetObjectForVisualizer(
   BOOL* b
);
```

```csharp
int CanSetObjectForVisualizer(
   out int b
);
```

## <a name="parameters"></a>Parametri
`b`\
out Diverso da zero ( `TRUE` ) se l'oggetto nel visualizzatore può essere aggiornato, zero ( `FALSE` ) se non è possibile.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un oggetto potrebbe non essere modificabile se è associato alla memoria di sola lettura, ad esempio.

## <a name="see-also"></a>Vedi anche
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
