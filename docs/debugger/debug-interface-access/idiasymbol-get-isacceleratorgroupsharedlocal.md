---
description: Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa del gruppo nel codice compilato per un acceleratore C++ AMP.
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8da1e0e8672fb0c10769ca448556f0007fe44014
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147303"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa del gruppo nel codice compilato per un acceleratore C++ AMP.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Puntatore a un valore `BOOL` che indica se il simbolo corrisponde a una variabile locale condivisa del gruppo nel codice compilato per un acceleratore C++ amp. Se `TRUE` , i `get_baseDataSlot` `get_baseDataOffset` metodi e possono essere usati per ottenere le informazioni sul percorso di archiviazione per la variabile.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)
