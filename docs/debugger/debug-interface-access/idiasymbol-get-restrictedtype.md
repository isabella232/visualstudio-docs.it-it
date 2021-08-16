---
description: Specifica se il puntatore this è contrassegnato come con restrizioni.
title: IDiaSymbol::get_restrictedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7b03696ccfc9c158cea1b626e40c62cb96e831edf278c9569699e70d26b7bc0e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420566"
---
# <a name="idiasymbolget_restrictedtype"></a>IDiaSymbol::get_restrictedType
Specifica se il `this` puntatore è contrassegnato come con restrizioni.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_restrictedType(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Puntatore a `BOOL` un oggetto che specifica se il `this` puntatore è contrassegnato come con restrizioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
