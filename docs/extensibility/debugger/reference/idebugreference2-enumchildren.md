---
description: Ottiene un elenco di elementi figlio selezionati di un riferimento.
title: Interfaccia IDebugReference2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27541d1a9f238acbe626a67520868bfd882833717487ea253c37a64fdf8a1f21
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338618"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Ottiene un elenco di elementi figlio selezionati di un riferimento. Riservato per utilizzi futuri.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di flag [dell'enumerazione DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) che specifica quali campi [](../../../extensibility/debugger/reference/debug-reference-info.md) nelle strutture DEBUG_REFERENCE_INFO enumerate devono essere compilati.

`dwRadix`\
[in] Radice da utilizzare per la formattazione di qualsiasi informazione numerica.

`dwAttribFilter`\
[in] Combinazione di flag [dell'enumerazione DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) utilizzata come filtro in combinazione con il parametro per selezionare le strutture `pszNameFilter` da enumerare.

`pszNameFilter`\
[in] Stringa che specifica un filtro, ad esempio "MyX", usata in combinazione con il parametro per selezionare `dwAttribFilter` le strutture da enumerare.

`dwTimeout`\
[in] Tempo massimo di attesa, in millisecondi, prima della restituzione da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.

`ppEnum`\
[out] Restituisce un [oggetto IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) che contiene un elenco delle proprietà figlio richieste.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="see-also"></a>Vedi anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
