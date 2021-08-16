---
description: Recupera l'indirizzo RVA (Relative Virtual Address) di una destinazione thunk.
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f5912453c7104b9d6b5f15c46c195413f7d82194505d203a8256fb124409d2a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362961"
---
# <a name="idiasymbolget_targetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Recupera l'indirizzo RVA (Relative Virtual Address) di una destinazione thunk.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_targetRelativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'RVA di una destinazione thunk.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Questa proprietà è valida solo se il simbolo è un [valore di enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) di `SymTagThunk` .

 Un "thunk" è un frammento di codice che esegue la conversione tra uno spazio indirizzi di memoria a 32 bit (noto anche come spazio indirizzi flat) e uno spazio indirizzi a 16 bit (noto come spazio indirizzi segmentato).

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
