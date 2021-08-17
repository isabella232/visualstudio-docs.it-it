---
description: Ottiene la DEBUG_PROPERTY_INFO che descrive una proprietà.
title: IDebugProperty2::GetPropertyInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26ffe65e84f8c878644e3fd4cec7fa3ad16ba544c221c8a02779870253d923df
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338709"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Ottiene la [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) che descrive una proprietà.

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
[in] Combinazione di valori [dell'DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica quali campi devono essere compilati nella `pPropertyInfo` struttura .

`nRadix`\
[in] Radice da utilizzare nella formattazione di qualsiasi informazione numerica.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per attendere a tempo indeterminato.

`rgpArgs`\
[in, out] Riservato per un uso futuro; impostato su un valore Null.

`dwArgCount`\
[in] Riservato per un uso futuro; impostato su zero.

`pPropertyInfo`\
[out] Struttura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) che viene compilata con la descrizione della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
