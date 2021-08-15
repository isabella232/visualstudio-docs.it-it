---
description: Recupera il nome file della libreria o del file oggetto da cui è stato caricato l'oggetto.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5255cb7aaae56b73e20536c570dab2b727e6160835af93ef83c3e1c003f03816
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454687"
---
# <a name="idiasymbolget_libraryname"></a>IDiaSymbol::get_libraryName
Recupera il nome file della libreria o del file oggetto da cui è stato caricato l'oggetto.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_libraryName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il nome file della libreria o del file oggetto da cui è stato caricato l'oggetto.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
