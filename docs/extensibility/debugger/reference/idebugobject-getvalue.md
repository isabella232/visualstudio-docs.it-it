---
description: Ottiene il valore dell'oggetto come una serie consecutiva di byte.
title: Interfaccia IDebugObject::GetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 232fdb9165121921a0828abc4dbd2de0ee286f47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126908"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Ottiene il valore dell'oggetto come una serie consecutiva di byte.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parametri
`pValue`\
[in, out] Matrice compilata con una serie consecutiva di byte che rappresenta il valore dell'oggetto .

`nSize`\
[in] Numero massimo di byte da recuperare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Ottenere il numero totale di byte di valore che possono essere recuperati chiamando il [metodo GetSize.](../../../extensibility/debugger/reference/idebugobject-getsize.md)

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
