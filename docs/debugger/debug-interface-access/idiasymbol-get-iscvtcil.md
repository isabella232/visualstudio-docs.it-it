---
title: IDiaSymbol::get_isCVTCIL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isCVTCIL method
ms.assetid: 711b81fd-9549-44dc-9761-5eb862ed64c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a4741c4f3a13b77dd871cefdb7a9d6430250b98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740265"
---
# <a name="idiasymbolget_iscvtcil"></a>IDiaSymbol::get_isCVTCIL
Recupera un flag che indica se il modulo è stato convertito da un modulo di Common Intermediate Language (CIL) a un modulo nativo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isCVTCIL(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se il modulo è stato convertito da CIL a codice nativo; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Questa proprietà è disponibile dal tipo di simbolo `SymTagCompilandDetails` (vedere [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md).

## <a name="requirements"></a>Requisiti

|Requisiti|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)