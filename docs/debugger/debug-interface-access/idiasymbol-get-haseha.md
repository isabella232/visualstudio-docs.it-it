---
title: IDiaSymbol::get_hasEHa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f010fee3243a9ce202451fc9cc5cff1ed908118
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740523"
---
# <a name="idiasymbolget_haseha"></a>IDiaSymbol::get_hasEHa
Recupera un flag che specifica se la funzione contiene la gestione delle eccezioni asincrona (strutturata).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasEHa(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se la funzione ha una gestione asincrona delle eccezioni. in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 È possibile combinare la gestione delle eccezioni asincrona o strutturata C++con la gestione delle eccezioni di tipo, ma è necessaria una specifica opzione del compilatore,/EHA, per abilitarla.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)