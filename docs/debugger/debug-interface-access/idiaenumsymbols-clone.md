---
description: Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore dei simboli corrente.
title: IDiaEnumSymbols::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e4835b4bfecccb6c83bc5532663d5d7b6d86dedb7ccdd8b48def273f11e04efe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455095"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>Parametri
 ppenum

[out] Restituisce un [oggetto IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene un duplicato dell'enumeratore. I simboli non vengono duplicati, ma solo l'enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
