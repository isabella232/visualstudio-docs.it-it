---
description: Recupera un flag che indica se il simbolo corrisponde al simbolo dell'intervallo di definizione per il componente tag di una variabile puntatore nel codice compilato per un C++ AMP Acceleratore.
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b65e31e2e6d86711b576023ff0f70877e29cdd03
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031210"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Recupera un flag che indica se il  simbolo corrisponde al simbolo dell'intervallo di definizione per il componente tag di una variabile puntatore nel codice compilato per un C++ AMP Acceleratore. Il simbolo dell'intervallo di definizioni è la posizione di una variabile per un intervallo di indirizzi.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Puntatore a un `BOOL` oggetto che indica se il simbolo corrisponde al simbolo dell'intervallo di definizione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
