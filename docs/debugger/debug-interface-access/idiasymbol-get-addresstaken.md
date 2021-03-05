---
description: Recupera un flag che indica se un altro simbolo fa riferimento all'indirizzo di questo simbolo.
title: IDiaSymbol::get_addressTaken | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2db653509b0afa40f3b59e1a4a6232763da6ef1f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156566"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
Recupera un flag che indica se un altro simbolo fa riferimento all'indirizzo di questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se un altro simbolo fa riferimento a questo indirizzo. in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `B` fa riferimento a `A` . Pertanto, `A` il metodo del simbolo `get_addressTaken` restituisce `TRUE` .

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
