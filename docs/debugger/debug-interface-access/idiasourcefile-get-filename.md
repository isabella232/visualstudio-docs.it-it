---
description: Recupera il nome del file di origine.
title: IDiaSourceFile::get_fileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_fileName method
ms.assetid: a5cb8927-23c6-469e-8f78-f2787d85dba4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f005187f4256f773b43dc0ae88a5bf586e4206266476ca9efc4efc7f0008e4c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454903"
---
# <a name="idiasourcefileget_filename"></a>IDiaSourceFile::get_fileName
Recupera il nome del file di origine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_fileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il nome del file di origine.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
