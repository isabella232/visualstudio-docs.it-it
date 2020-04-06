---
title: Proprietà IDebugProperty2::GetPropertyInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ec1c3e29e0dbb6ca069dec696e6645a159ec7e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721373"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Ottiene la [struttura DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) che descrive una proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPropertyInfo ( 
   DEBUGPROP_INFO_FLAGS dwFields,
   DWORD                nRadix,
   DWORD                dwTimeout,
   IDebugReference2**   rgpArgs,
   DWORD                dwArgCount,
   DEBUG_PROPERTY_INFO* pPropertyInfo
);
```

```cpp
int GetPropertyInfo ( 
   enum_DEBUGPROP_INFO_FLAGS dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_PROPERTY_INFO[]     pPropertyInfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di valori dell'enumerazione [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica quali campi `pPropertyInfo` devono essere compilati nella struttura.

`nRadix`\
[in] Radice da utilizzare nella formattazione di qualsiasi informazione numerica.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per attendere a tempo indeterminato.

`rgpArgs`\
[in, out] Riservato per uso futuro; impostato su un valore null.

`dwArgCount`\
[in] Riservato per uso futuro; impostato su zero.

`pPropertyInfo`\
[fuori] Struttura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) compilata con la descrizione della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
