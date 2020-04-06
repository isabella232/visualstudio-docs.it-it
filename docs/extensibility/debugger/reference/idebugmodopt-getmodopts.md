---
title: Proprietà IDebugModOpt::GetModOpts . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727054"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Recupera un elenco di modificatori facoltativi.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in] Numero di elementi da restituire.

`rgelt`\
[fuori] Restituisce una matrice che contiene le opzioni.

`pceltFetched`\
[in, out] Numero di elementi restituiti nella `rgelt` matrice.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
