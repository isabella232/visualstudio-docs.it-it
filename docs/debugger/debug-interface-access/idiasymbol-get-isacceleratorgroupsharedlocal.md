---
description: Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa di gruppo nel codice compilato per un acceleratore C++ AMP.
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e334766cb5659d4f94c7db2f5fbdc0e4ab68a2ebb79e64a877c77c6e0a125dad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379870"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa di gruppo nel codice compilato per un acceleratore C++ AMP.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Puntatore a un oggetto che indica se il simbolo corrisponde a una variabile locale condivisa di gruppo nel codice compilato per un C++ AMP `BOOL` acceleratore. Se `TRUE` , è possibile usare i metodi e per ottenere le informazioni sulla posizione di archiviazione per la `get_baseDataSlot` `get_baseDataOffset` variabile.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)
