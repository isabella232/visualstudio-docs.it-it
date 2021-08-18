---
description: Recupera un flag che specifica se per il tipo di dati definito dall'utente sono definiti operatori di assegnazione.
title: IDiaSymbol::get_hasAssignmentOperator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAssignmentOperator method
ms.assetid: fb1acb9c-4500-4343-a590-0395789e4040
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7d3b9084249d2a0ae78f1df05374cd1c021f8ff5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121513"
---
# <a name="idiasymbolget_hasassignmentoperator"></a>IDiaSymbol::get_hasAssignmentOperator
Recupera un flag che specifica se per il tipo di dati definito dall'utente sono definiti operatori di assegnazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasAssignmentOperator ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se per il tipo di dati definito dall'utente sono definiti operatori di assegnazione; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
