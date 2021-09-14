---
description: Recupera un file di origine tramite un indice.
title: IDiaEnumSourceFiles::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0a47a77766489bbc99441cfdb95a25e4473cbcc8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630095"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Recupera un file di origine tramite un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Parametri
 index

[in] Indice [dell'oggetto IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) da recuperare. L'indice è compreso nell'intervallo da 0 a -1, dove viene restituito dal metodo `count` `count` [IDiaEnumSourceFiles::get_Count.](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)

 sourceFile

[out] Restituisce un [oggetto IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) che rappresenta il file di origine desiderato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
