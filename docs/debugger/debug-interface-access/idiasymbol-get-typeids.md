---
description: Recupera una matrice di valori di identificatore di tipo specifici del compilatore per questo simbolo.
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
ms.openlocfilehash: b3e3cd29c1cb00cfa2c01f1061487ed6a75852e4c771656efa2cf3ae94d150f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391648"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Recupera una matrice di valori di identificatore di tipo specifici del compilatore per questo simbolo.

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

[in] Dimensioni del buffer per contenere i dati.

 `pcTypeIds`

[out] Restituisce il numero di identificatori di tipo scritti `typeIds` oppure, `typeIds` se è , il numero totale di identificatori di tipo `NULL` disponibili.

 `typeIds[]`

[out] Matrice che deve essere compilata con gli identificatori di tipo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
