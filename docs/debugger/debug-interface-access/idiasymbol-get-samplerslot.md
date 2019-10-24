---
title: IDiaSymbol::get_samplerSlot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 41c751ba-81be-4bd3-838f-8373fc146157
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a311b7139ba9b6d93eac1d50308db2e951c5c4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739378"
---
# <a name="idiasymbolget_samplerslot"></a>IDiaSymbol::get_samplerSlot
Recupera lo slot del campionatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_samplerSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un `DWORD` che include lo slot del campionatore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)