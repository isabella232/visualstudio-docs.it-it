---
description: Recupera una matrice di valori di identificatori di tipo specifici del compilatore per questo simbolo.
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0324891d5819ea850d1a4cd21464778a93ea78ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036047"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Recupera una matrice di valori di identificatori di tipo specifici del compilatore per questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parametri
 `cTypeIds`

[in] Dimensione del buffer in cui contenere i dati.

 `pcTypeIds`

[out] Restituisce il numero di identificatori di tipo scritti oppure, se `typeIds` è , il numero totale di identificatori di tipo `typeIds` `NULL` disponibili.

 `typeIds[]`

[out] Matrice che deve essere compilata con gli identificatori di tipo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
