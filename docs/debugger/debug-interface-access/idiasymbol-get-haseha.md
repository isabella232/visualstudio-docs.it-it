---
description: Recupera un flag che specifica se la funzione contiene la gestione delle eccezioni asincrona (strutturata).
title: IDiaSymbol::get_hasEHa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bb5ed15f7ba88f114ec8923a5932a2890a5d2031440e3b50895d59e07f05a760
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420702"
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

[out] Restituisce `TRUE` se la funzione ha una gestione delle eccezioni asincrona; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 È possibile combinare la gestione delle eccezioni asincrona o strutturata con la gestione delle eccezioni di tipo C++, ma per abilitarla è necessaria un'opzione del compilatore specifica, /EHa.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
