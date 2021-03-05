---
description: Recupera un flag che indica se il simbolo corrisponde al simbolo dell'intervallo di definizioni per il componente tag di una variabile puntatore nel codice compilato per un acceleratore C++ AMP.
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f46618e0dddf788f106cfccd836d3e228835735
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156244"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Recupera un flag che indica se il simbolo corrisponde al *simbolo dell'intervallo di definizioni* per il componente tag di una variabile puntatore nel codice compilato per un acceleratore C++ amp. Il simbolo dell'intervallo di definizioni è il percorso di una variabile per un intervallo di indirizzi.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Puntatore a un valore `BOOL` che indica se il simbolo corrisponde al simbolo dell'intervallo di definizioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
