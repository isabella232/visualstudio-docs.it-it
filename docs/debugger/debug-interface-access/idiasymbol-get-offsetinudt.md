---
title: IDiaSymbol::get_offsetInUdt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offsetInUdt method
ms.assetid: 442f20d9-9d6a-44a1-83fb-c3f8c14b6c97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0eeffba743d7fae1d473c45eb350fbfc8bcd0b9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739567"
---
# <a name="idiasymbolget_offsetinudt"></a>IDiaSymbol::get_offsetInUdt
Recupera l'offset all'inizio di un tipo definito dall'utente (UDT) di un membro nel tipo definito dall'utente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_offsetInUdt( 
   DWORD* pRetVal)
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'offset in byte della posizione del simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Questa funzione viene utilizzata solo nei record locali in una compilazione ottimizzata.

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)