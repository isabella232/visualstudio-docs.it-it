---
title: Proprietà IDebugObject::GetValue . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726548"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Ottiene il valore dell'oggetto come serie consecutive di byte.

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
[in, out] Matrice compilata con una serie consecutiva di byte che rappresentano il valore dell'oggetto.

`nSize`\
[in] Numero massimo di byte da recuperare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Ottiene il numero totale di byte di valore che possono essere recuperati chiamando il [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
