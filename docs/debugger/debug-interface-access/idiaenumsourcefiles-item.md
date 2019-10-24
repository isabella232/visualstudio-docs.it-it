---
title: 'IDiaEnumSourceFiles:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 352c9516180c0ee0021fca4e0913f154f3b8d46f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744085"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Recupera un file di origine per mezzo di un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Parametri
 indice

in Indice dell'oggetto [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` viene restituito dal metodo [IDiaEnumSourceFiles:: get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) .

 sourceFile

out Restituisce un oggetto [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) che rappresenta il file di origine desiderato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)