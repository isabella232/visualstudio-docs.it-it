---
description: Imposta il valore dell'oggetto da una serie consecutiva di byte.
title: IDebugObject::SetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68e2f923088ce16958ffbcd197baaf76f16c5733
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034877"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Imposta il valore dell'oggetto da una serie consecutiva di byte.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Parametri
`pValue`\
[in] Matrice di byte che rappresenta il nuovo valore.

`nSize`\
[in] Dimensione del valore in byte.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 I valori nella matrice vengono copiati in questo [oggetto IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) sostituendo qualsiasi valore esistente. Le dimensioni del nuovo valore possono essere maggiori o minori del valore esistente. Non `IDebugObject` può essere un riferimento Null.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [Getvalue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
