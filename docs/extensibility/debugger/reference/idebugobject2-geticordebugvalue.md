---
description: Ottiene un oggetto di codice gestito che rappresenta il valore associato a questo oggetto .
title: IDebugObject2::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 054bf154aaa5ceadd386e4b3ff7e0b9a15f62e77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043114"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Ottiene un oggetto di codice gestito che rappresenta il valore associato a questo oggetto .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parametri
`ppUnk`\
[out] `IUnknown` Interfaccia che rappresenta questo alias. È possibile eseguire query su questa interfaccia `ICorDebugValue` per l'interfaccia.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 `ICorDebugValue`L'oggetto è un'interfaccia di Common Language Runtime che rappresenta un valore.

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
