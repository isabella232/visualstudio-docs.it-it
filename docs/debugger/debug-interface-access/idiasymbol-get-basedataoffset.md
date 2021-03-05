---
description: Recupera l'offset dei dati di base.
title: IDiaSymbol::get_baseDataOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb2ff5ed-9293-4c37-9741-654058b571c5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1394f5d5d19431ed6d1db6860edd171e164ad35
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162280"
---
# <a name="idiasymbolget_basedataoffset"></a>IDiaSymbol::get_baseDataOffset
Recupera l'offset dei dati di base.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_baseDataOffset(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un oggetto `DWORD` che include l'offset dei dati di base.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
