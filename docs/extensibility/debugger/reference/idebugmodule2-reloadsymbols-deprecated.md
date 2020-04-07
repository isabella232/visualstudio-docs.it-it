---
title: IDebugModule2::ReloadSymbols_Deprecated . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726927"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETO. NON UTILIZZARE. Ricarica i simboli per questo modulo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Parametri
`pszUrlToSymbols`\
[in] Percorso dell'archivio simboli.

`pbstrDebugMessage`\
[fuori] Restituisce un messaggio informativo, ad esempio uno stato o un messaggio di errore, visualizzato a destra del nome del modulo nella finestra Moduli.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Un motore di `E_FAIL`debug deve sempre restituire .

## <a name="remarks"></a>Osservazioni
 Questo metodo non è più supportato. Implementare invece il metodo [LoadSymbols.Implement](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) the LoadSymbols method instead.

## <a name="see-also"></a>Vedere anche
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
