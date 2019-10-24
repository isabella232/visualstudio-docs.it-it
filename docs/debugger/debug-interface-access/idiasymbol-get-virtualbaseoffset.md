---
title: IDiaSymbol::get_virtualBaseOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseOffset method
ms.assetid: 103b034f-36c4-42d5-aa34-1449a1e66d03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c72c605b47a5f34542b46cae9943b03c7072b1f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738861"
---
# <a name="idiasymbolget_virtualbaseoffset"></a>IDiaSymbol::get_virtualBaseOffset
Recupera l'offset nella tabella delle funzioni virtuali di una funzione virtuale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_virtualBaseOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'offset nella tabella delle funzioni virtuali di una funzione virtuale.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)