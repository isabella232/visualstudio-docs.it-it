---
description: Recupera un elenco degli elementi figlio della proprietà .
title: IDebugProperty2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b38f7ca508edbd33feffe23fe8a09126cbdb7434
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071340"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera un elenco degli elementi figlio della proprietà .

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
[in] Combinazione di flag [dell'enumerazione DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica quali campi [](../../../extensibility/debugger/reference/debug-property-info.md) nelle strutture DEBUG_PROPERTY_INFO enumerate devono essere compilati.

`dwRadix`\
[in] Specifica la radice da utilizzare per la formattazione di qualsiasi informazione numerica.

`guidFilter`\
[in] GUID del filtro utilizzato con i `dwAttribFilter` parametri e per selezionare gli elementi figlio da `pszNameFilter` `DEBUG_PROPERTY_INFO` enumerare. Ad esempio, `guidFilterLocals` filtri per le variabili locali.

`dwAttribFilter`\
[in] Combinazione di flag [dell'enumerazione DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) che specifica il tipo di oggetti da enumerare, ad esempio per tutti i metodi che potrebbero `DBG_ATTRIB_METHOD` essere figli di questa proprietà. Utilizzato in combinazione con `guidFilter` i parametri `pszNameFilter` e .

`pszNameFilter`\
[in] Nome del filtro utilizzato con i `guidFilter` parametri e per selezionare gli elementi figlio da `dwAttribFilter` `DEBUG_PROPERTY_INFO` enumerare. Ad esempio, l'impostazione di questo parametro su "MyX" filtra tutti gli elementi figlio con il nome "MyX".

`dwTimeout`\
[in] Specifica il tempo massimo di attesa, in millisecondi, prima della restituzione da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.

`ppEnum`\
[out] Restituisce un [oggetto IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente un elenco delle proprietà figlio.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
