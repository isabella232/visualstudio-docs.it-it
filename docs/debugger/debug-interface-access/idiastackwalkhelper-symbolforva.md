---
title: IDiaStackWalkHelper::symbolForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90b157b0f5b09353ede1af1d344f1f9adf68debd
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464632"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Recupera il simbolo che contiene l'indirizzo virtuale specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT symbolForVA( 
   ULONGLONG     va,
   IDiaSymbol**  ppSymbol
);
```

#### <a name="parameters"></a>Parametri
 `va`

in Indirizzo virtuale contenuto nel simbolo richiesto. Il simbolo deve essere un oggetto, `SymTagFunctionType` ovvero un valore dell'enumerazione [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .

 `ppSymbol`

out Oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il simbolo in corrispondenza dell'indirizzo specificato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)