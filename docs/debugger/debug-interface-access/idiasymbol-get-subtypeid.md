---
title: IDiaSymbol::get_subTypeId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0f899920-4fc5-4de8-84a3-cd98c57bf124
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66c7a05ef6b8e90eda2b29bdbb7d33fcf25a2af2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739272"
---
# <a name="idiasymbolget_subtypeid"></a>IDiaSymbol::get_subTypeId
Recupera l'ID del sottotipo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_subTypeId(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un `DWORD` che include l'ID del sottotipo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)