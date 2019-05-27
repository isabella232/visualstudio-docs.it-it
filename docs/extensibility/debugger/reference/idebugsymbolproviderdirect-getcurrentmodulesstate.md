---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d67c266295a69fe3f045aa5329b0f6667766128
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207023"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Recupera le informazioni relative al gruppo di simboli di cui il provider di simboli è un membro.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCurrentModulesState(
    DWORD*          pState,
    unsigned long * count
);
```

```csharp
int GetCurrentModulesState(
    out uint pState,
    out uint count
);
```

## <a name="parameters"></a>Parametri
`pState`\
[out] Lo stato del gruppo di provider di simboli.

`count`\
[out] Numero di moduli del gruppo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Lo stato viene modificato ogni volta che un modulo viene aggiunto a o rimosso da, il gruppo di simboli. Di conseguenza, questo metodo può essere utilizzato per rilevare se un gruppo di simboli è stato modificato.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)