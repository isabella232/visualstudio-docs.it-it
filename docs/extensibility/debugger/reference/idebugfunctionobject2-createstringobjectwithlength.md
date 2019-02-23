---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02ee13b62a2238624f1c6d42c52bf67db2ceaae4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710409"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Crea un oggetto stringa che contiene la lunghezza specificata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

#### <a name="parameters"></a>Parametri
 `pcstrString`

 [in] Il valore di stringa per l'oggetto stringa.

 `uiLength`

 [in] La lunghezza della stringa in byte.

 `ppObject`

 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta l'oggetto stringa appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)