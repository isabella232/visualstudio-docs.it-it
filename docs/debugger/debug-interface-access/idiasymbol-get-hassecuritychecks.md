---
title: IDiaSymbol::get_hasSecurityChecks | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a760389f589dc14e8a768991323c0419dac527
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "64808706"
---
# <a name="idiasymbolgethassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Recupera un flag che specifica se il modulo o la funzione è stato compilato con i controlli di sicurezza di sovraccarico del buffer (ad esempio, il [/GS (controllo sicurezza Buffer)](/cpp/build/reference/gs-buffer-security-check) opzione del compilatore).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se la funzione dispone di controlli di sicurezza; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|DIA2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (controllo sicurezza buffer)](/cpp/build/reference/gs-buffer-security-check)