---
description: Recupera un flag che indica se il segmento può essere modificato.
title: IDiaSegment::get_write | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_write method
ms.assetid: 5fcda988-6be1-4b2f-8660-b59aa78fc35d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e6d718c187c862febe20d94182b858e993599306
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134265"
---
# <a name="idiasegmentget_write"></a>IDiaSegment::get_write
Recupera un flag che indica se il segmento può essere modificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_write ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se il segmento può essere scritto; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
