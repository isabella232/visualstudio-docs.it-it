---
description: Ottiene l'indirizzo di debug che segue un indirizzo di debug specificato in un metodo.
title: IDebugSymbolProvider::GetNextAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b1e8e1d954fddae1887e9a2aa488f5ecacbe503547c3b026d4da0294f4aba6d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448767"
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

## <a name="parameters"></a>Parametri
`pAddress`\
[in] Indirizzo di debug specificato.

`fStatementOnly`\
[in] Se TRUE, limita gli indirizzi di debug a una singola istruzione.

`ppAddress`\
[out] Restituisce l'indirizzo di debug successivo.

## <a name="return-value"></a>Valore restituito
 Restituisce un oggetto `HRESULT` valido, in genere S_OK.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
