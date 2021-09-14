---
description: Recupera un flag che specifica se il simbolo di dati è stato suddiviso in un'aggregazione o in una raccolta di altri simboli. il compilatore considera i simboli come entità separate, anche se fanno effettivamente parte di un simbolo più grande.
title: IDiaSymbol::get_isSplitted | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c025460f04cbd2d9eb5546f434ff990584fa7e26
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709952"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
Recupera un flag che specifica se il simbolo di dati è stato suddiviso in un'aggregazione o in una raccolta di altri simboli. il compilatore considera i simboli come entità separate, anche se fanno effettivamente parte di un simbolo più grande.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se il simbolo è stato suddiviso in un'aggregazione di simboli; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Il [metodo IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) restituisce per tutti i simboli `TRUE` che fanno parte di un simbolo di divisione.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)
