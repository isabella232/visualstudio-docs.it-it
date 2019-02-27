---
title: IDiaSymbol::get_baseSymbolId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8880d207a41418e12cab4374578fea4f3c4f338c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622449"
---
# <a name="idiasymbolgetbasesymbolid"></a>IDiaSymbol::get_baseSymbolId
Recupera l'ID di simbolo da cui si basa il puntatore del mouse.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_baseSymbolId(
   DWORD *pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Un puntatore a un `DWORD` che contiene l'ID di simbolo da cui si basa il puntatore del mouse.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)