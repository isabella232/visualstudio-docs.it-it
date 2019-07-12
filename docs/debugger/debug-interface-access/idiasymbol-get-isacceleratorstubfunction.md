---
title: IDiaSymbol::get_isAcceleratorStubFunction | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbcfbfcd1e95a45388d0b7c0626f1cd529607ce4
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836629"
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Indica se il simbolo corrisponde a un simbolo di funzione di primo livello per uno shader compilato per un tasto di scelta rapida che corrisponde a un `parallel_for_each` chiamare.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Un puntatore a un `BOOL` che indica se il simbolo corrisponde a un simbolo di funzione di primo livello per uno shader compilato per un tasto di scelta rapida che corrisponde a un `parallel_for_each` chiamare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)