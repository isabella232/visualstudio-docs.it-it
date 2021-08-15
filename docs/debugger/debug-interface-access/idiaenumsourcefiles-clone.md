---
description: Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore dei file di origine corrente.
title: IDiaEnumSourceFiles::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fd4749b4eb67552155b54d8c1e46c95f60ca625bc0148a56d9f82e92f9dd6323
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455103"
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Clone ( 
   IDiaEnumSourceFiles** ppenum
);
```

#### <a name="parameters"></a>Parametri
 ppenum

[out] Restituisce un [oggetto IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) che contiene un duplicato dell'enumeratore. I file di origine non vengono duplicati, ma solo l'enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
