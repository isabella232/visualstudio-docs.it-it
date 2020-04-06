---
title: Proprietà IDebugProperty2::EnumChildren . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721519"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera un elenco degli elementi figlio della proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di flag dell'enumerazione [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica quali campi nelle strutture [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) enumerate devono essere compilate.

`dwRadix`\
[in] Specifica la radice da utilizzare nella formattazione di qualsiasi informazione numerica.

`guidFilter`\
[in] GUID del filtro utilizzato `dwAttribFilter` `pszNameFilter` con i `DEBUG_PROPERTY_INFO` parametri e per selezionare gli elementi figlio da enumerare. Ad esempio, `guidFilterLocals` i filtri per le variabili locali.

`dwAttribFilter`\
[in] Combinazione di flag [dall'enumerazione DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) che specifica il tipo `DBG_ATTRIB_METHOD` di oggetti da enumerare, ad esempio per tutti i metodi che potrebbero essere figli di questa proprietà. Utilizzato in combinazione `guidFilter` `pszNameFilter` con i parametri e .

`pszNameFilter`\
[in] Nome del filtro utilizzato `guidFilter` con `dwAttribFilter` i parametri `DEBUG_PROPERTY_INFO` e per selezionare gli elementi figlio da enumerare. Ad esempio, l'impostazione di questo parametro su "MyX" filtri per tutti gli elementi figlio con il nome "MyX".

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per attendere a tempo indeterminato.

`ppEnum`\
[fuori] Restituisce un [oggetto IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente un elenco delle proprietà figlio.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
