---
description: Recupera un elenco degli stack frame per questo thread.
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07ede35a1014d9c192740af58e5a5bdcc4ff93851c8204905384955a77da2b00
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389514"
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
[in] Combinazione di flag [dell'FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) che specifica quali campi delle strutture [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) devono essere compilati. Specificare il `FIF_FUNCNAME_FORMAT` flag per formattare il nome della funzione in un'unica stringa.

`nRadix`\
[in] Radice utilizzata nella formattazione delle informazioni numeriche nell'enumeratore.

`ppEnum`\
[out] Restituisce un [oggetto IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) che contiene un elenco di [strutture FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) che descrivono la stack frame.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 I frame del thread vengono enumerati in ordine, con il frame corrente enumerato per primo e il frame meno recente enumerato per ultimo.

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
