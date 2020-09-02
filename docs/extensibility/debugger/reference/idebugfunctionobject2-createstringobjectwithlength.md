---
title: 'IDebugFunctionObject2:: CreateStringObjectWithLength | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 937d325f8637a3260121def189d472dcfb3e1309
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728473"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Crea un oggetto stringa con la lunghezza specificata.

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

## <a name="parameters"></a>Parametri
`pcstrString`\
in Valore stringa per l'oggetto stringa.

`uiLength`\
in Lunghezza della stringa in byte.

`ppObject`\
out Restituisce un oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto stringa appena creato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
