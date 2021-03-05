---
description: Recupera il nome del file di libreria o oggetto da cui è stato caricato l'oggetto.
title: IDiaSymbol::get_libraryName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_libraryName method
ms.assetid: d04ddd9a-812d-46e4-bd39-28bdf3edfb70
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e717e1794531114d7b68966ef19bdbb2158bfe60
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161991"
---
# <a name="idiasymbolget_libraryname"></a>IDiaSymbol::get_libraryName
Recupera il nome del file di libreria o oggetto da cui è stato caricato l'oggetto.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_libraryName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il nome del file di libreria o oggetto da cui è stato caricato l'oggetto.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
