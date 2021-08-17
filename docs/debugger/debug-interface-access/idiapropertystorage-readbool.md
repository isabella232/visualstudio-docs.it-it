---
description: Legge i valori BOOL in un set di proprietà.
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2b7e04906d5e809538c5cb99b9b43d66701020b5d387ff3ab824367b72a94508
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344996"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Legge i `BOOL` valori in un set di proprietà.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Parametri
 `id`

[in] Identificatore della proprietà da leggere ( `PROPID` è definito in WTypes.h come `ULONG` ).

 `pValue`

[out] Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, `S_OK` restituisce ; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `BOOL` .

## <a name="remarks"></a>Commenti
 Per risultati coerenti, interpretare il `BOOL` valore in modo che i valori diversi da zero siano e zero sia `TRUE` `FALSE` .

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
