---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67afbf985a8fb9934c1a105d1620becc80f00535
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347421"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
Recupera le informazioni sui moduli del gruppo di simboli.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCurrentModulesInfo(
   unsigned long * pCount,
   GUID *          ppGuids,
   DWORD *         pADIds,
   DWORD *         pCurrentState,
   IUnknown **     ppCDModItfs
);
```

```csharp
int GetCurrentModulesInfo(
   uint       pCount,
   Guid       ppGuids,
   uint       pADIds,
   uint       pCurrentState,
   out object ppCDModItfs
);
```

## <a name="parameters"></a>Parametri
`pCount`\
[in] Numero di moduli nel `ppGuids` matrice.

`ppGuids`\
[in] Matrice che contiene gli identificatori univoci per i moduli.

`pADIds`\
[in] Identificatori per i domini applicazione.

`pCurrentState`\
[in] Stato corrente del gruppo di simboli.

`ppCDModItfs`\
[out] Restituisce un oggetto che contiene i moduli nel gruppo di simboli.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)