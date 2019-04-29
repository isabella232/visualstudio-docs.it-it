---
title: IDebugSymbolProvider::GetNextAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 574111db390388ee1d0c572a3a8825c3a2ae9469
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915670"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Ottiene l'indirizzo di debug che segue un indirizzo di debug specificato in un metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

#### <a name="parameters"></a>Parametri
 `pAddress`

 [in] Indirizzo di debug specificato.

 `fStatementOnly`

 [in] Se TRUE, limita gli indirizzi di debug per una singola istruzione.

 `ppAddress`

 [out] Restituisce l'indirizzo di debug successiva.

## <a name="return-value"></a>Valore restituito
 Restituisce un valore valido `HRESULT`, in genere S_OK.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)