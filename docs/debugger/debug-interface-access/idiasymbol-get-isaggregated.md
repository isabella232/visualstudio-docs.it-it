---
description: Recupera un flag che specifica se il simbolo di dati fa parte di un'aggregazione o di una raccolta di simboli; Il compilatore considera i simboli aggregati come entità separate, ma fanno effettivamente parte di un singolo simbolo più grande.
title: IDiaSymbol::get_isAggregated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1a870a6e868848f0d2c5b4c597440bc5214df31cb951fe8259cec633afc5306b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420678"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
Recupera un flag che specifica se il simbolo di dati fa parte di un'aggregazione o di una raccolta di simboli; Il compilatore considera i simboli aggregati come entità separate, ma fanno effettivamente parte di un singolo simbolo più grande.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se i dati fanno parte di un'aggregazione di simboli suddivisi da un simbolo padre; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Il [metodo IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) è per il simbolo padre `TRUE` dei simboli aggregati.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)
