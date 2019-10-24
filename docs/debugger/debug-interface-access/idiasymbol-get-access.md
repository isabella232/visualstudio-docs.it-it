---
title: IDiaSymbol::get_access | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_access method
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8f476a95215eda69a3655540891017eac2c88e4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741095"
---
# <a name="idiasymbolget_access"></a>IDiaSymbol::get_access
Recupera il modificatore di accesso di un membro di classe.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_access ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un valore dall'enumerazione Enumerazione [CV_access_e](../../debugger/debug-interface-access/cv-access-e.md) che specifica il modificatore di accesso di un membro di classe.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)