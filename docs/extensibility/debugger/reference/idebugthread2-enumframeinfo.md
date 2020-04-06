---
title: Proprietà IDebugThread2::EnumFrameInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718851"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera un elenco degli stack frame per questo thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`dwFieldSpec`\
[in] Combinazione di flag dell'enumerazione [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) che specifica quali campi delle strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) devono essere compilati. Specificare `FIF_FUNCNAME_FORMAT` il flag per formattare il nome della funzione in un'unica stringa.

`nRadix`\
[in] Radice utilizzata nella formattazione delle informazioni numeriche nell'enumeratore.

`ppEnum`\
[fuori] Restituisce un oggetto [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) che contiene un elenco di strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) che descrivono lo stack frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 I frame del thread vengono enumerati in ordine, con il frame corrente enumerato per primo e il frame meno recente enumerato per ultimo.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
