---
description: Recupera un flag che specifica se il tipo di dati definito dall'utente (UDT) è compresso.
title: IDiaSymbol::get_packed | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5e6cf89aa0bdd31b826ac8e73000c1bfa8c595c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161935"
---
# <a name="idiasymbolget_packed"></a>IDiaSymbol::get_packed
Recupera un flag che specifica se il tipo di dati definito dall'utente (UDT) è compresso.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_packed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se il tipo definito dall'utente è compresso; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Compresso significa che tutti i membri del tipo definito dall'utente vengono posizionati il più vicino possibile, senza spaziatura interna per allinearli ai limiti della memoria.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
