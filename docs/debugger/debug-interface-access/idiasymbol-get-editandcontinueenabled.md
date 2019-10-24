---
title: IDiaSymbol::get_editAndContinueEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_editAndContinueEnabled method
ms.assetid: cd703c64-9ff8-4654-8493-8cde9309cb22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2dd1d3c7cefe76feec5c65176450d0e73a77a25
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740691"
---
# <a name="idiasymbolget_editandcontinueenabled"></a>IDiaSymbol::get_editAndContinueEnabled
Recupera un flag che indica se il modulo è stato compilato con l'opzione del compilatore [/Z7,/Zi,/Zi (formato informazioni di debug)](/cpp/build/reference/z7-zi-zi-debug-information-format) .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_editAndContinueEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce `TRUE` se la funzionalità modifica e continuazione è stata abilitata durante la compilazione. in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/Z7, /Zi, /ZI (Formato informazioni di debug)](/cpp/build/reference/z7-zi-zi-debug-information-format)