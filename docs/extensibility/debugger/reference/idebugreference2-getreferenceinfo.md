---
description: Ottiene la DEBUG_REFERENCE_INFO che descrive un riferimento.
title: Interfaccia IDebugReference2::GetReferenceInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26445a6599e7e4b74b81de44cf891f95542d9c564a25a40944ed87eee6a46a2e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338553"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Ottiene la [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) che descrive un riferimento. Riservato per utilizzi futuri.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di flag [dell'enumerazione DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) che determinano i campi da completare nella [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura .

`nRadix`\
[in] Radice da utilizzare per la formattazione di qualsiasi informazione numerica.

`dwTimeout`\
[in] Tempo massimo di attesa, in millisecondi, prima della restituzione da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.

`rgpArgs`\
[in] Matrice di [oggetti IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md) Riservato per un uso futuro; impostato su un valore Null.

`dwArgCount`\
[in] Numero di argomenti di riferimento nella `rgpArgs` matrice. Riservato per un uso futuro; impostato su 0.

`pReferenceInfo`\
[out] Struttura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) che viene compilata con una descrizione della proprietà.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="see-also"></a>Vedi anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
