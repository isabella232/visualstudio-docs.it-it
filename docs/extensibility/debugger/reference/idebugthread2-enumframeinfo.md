---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 584c7ba10ac9eb05268f50ecaffa8c47818f7977
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915545"
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

#### <a name="parameters"></a>Parametri
 `dwFieldSpec`

 [in] Una combinazione di flag dal [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumerazione che specifica quali campi della [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture sono da compilare. Specificare il `FIF_FUNCNAME_FORMAT` flag per formattare il nome della funzione in un'unica stringa.

 `nRadix`

 [in] Radice usati nella formattazione di informazioni numeriche nell'enumeratore.

 `ppEnum`

 [out] Restituisce un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) oggetto che contiene un elenco delle [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture che descrivono lo stack frame.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Frame del thread vengono enumerati in ordine, con il fotogramma corrente enumerata prima e il meno recente enumerati ultima.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)