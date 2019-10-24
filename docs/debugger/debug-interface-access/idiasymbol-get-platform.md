---
title: 'IDiaSymbol:: get_Platform | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a86e7b6b75e0689ccd98a2cab2ed9ef93188312
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739495"
---
# <a name="idiasymbolget_platform"></a>IDiaSymbol::get_platform
Recupera il tipo di piattaforma per cui è stato compilato modulo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_platform ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un valore dall'enumerazione Enumerazione [CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) che specifica il tipo di piattaforma per il quale è stato compilato il modulo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)