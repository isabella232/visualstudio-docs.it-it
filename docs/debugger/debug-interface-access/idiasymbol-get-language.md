---
description: Recupera la lingua dell'origine.
title: IDiaSymbol::get_language | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06bdf7fdbda25d383084a0c53b224ccb5b8c64d12af79096e6edcf7fbb68e40e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379838"
---
# <a name="idiasymbolget_language"></a>IDiaSymbol::get_language
Recupera la lingua dell'origine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_language ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un valore [dall'enumerazione CV_CFL_LANG enumeration](../../debugger/debug-interface-access/cv-cfl-lang.md) che specifica la lingua dell'origine.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione CV_CFL_LANG](../../debugger/debug-interface-access/cv-cfl-lang.md)
