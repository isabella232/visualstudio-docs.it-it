---
description: Recupera un flag che specifica se la funzione contiene un valore restituito dall'istruzione di interrupt, ad esempio il codice assembly X86 iret'.
title: IDiaSymbol::get_interruptReturn | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_interruptReturn method
ms.assetid: 9665da6c-4cc0-41d7-b2e2-0d9e50174cf8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5167627f840d7d9121940179088e33e4d0697a36
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044214"
---
# <a name="idiasymbolget_interruptreturn"></a>IDiaSymbol::get_interruptReturn
Recupera un flag che specifica se la funzione contiene un valore restituito dall'istruzione interrupt, ad esempio il codice assembly `iret` X86.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_interruptReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se la funzione restituisce un'istruzione di interrupt; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
