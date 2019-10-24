---
title: IDiaSymbol::get_optimizedCodeDebugInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 590603e0fd44d8ee6da84790a98cfd8ef8be0b98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739547"
---
# <a name="idiasymbolget_optimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
Recupera un flag che indica se la funzione contiene informazioni di debug specifiche per il codice ottimizzato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_optimizedCodeDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se la funzione o l'etichetta ottimizzata contiene informazioni di debug; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)