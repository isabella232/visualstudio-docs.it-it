---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5a24a136bb9c04366449a91d825ddbecff2957
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740316"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Recupera un flag che indica se il simbolo corrisponde al *simbolo dell'intervallo di definizioni* per il componente tag di una variabile puntatore nel codice compilato per C++ un acceleratore amp. Il simbolo dell'intervallo di definizioni è il percorso di una variabile per un intervallo di indirizzi.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Puntatore a un `BOOL` che indica se il simbolo corrisponde al simbolo dell'intervallo di definizioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)