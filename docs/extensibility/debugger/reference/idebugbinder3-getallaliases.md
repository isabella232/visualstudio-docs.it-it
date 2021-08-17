---
description: Questo metodo recupera un elenco di alias dal programma.
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72e8b174888e2484a1b065268045a7bf33194957a909fb9ec71dc7c30a716fdd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293053"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Questo metodo recupera un elenco di alias dal programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Parametri
`uRequest`\
[in] Numero massimo di alias da restituire (specifica la lunghezza della matrice passata in `ppAliases` ).

`ppAliases`\
[in, out] Matrice da compilare con alias (se si tratta di un valore Null e è 0, il conteggio degli alias che possono essere restituiti `uRequest` verrà restituito da `puFetched` ).

`puFetched`\
[out] Restituisce il numero di alias ottenuti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
