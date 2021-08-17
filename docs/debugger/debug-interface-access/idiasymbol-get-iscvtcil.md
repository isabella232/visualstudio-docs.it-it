---
description: Recupera un flag che indica se il modulo è stato convertito da un modulo Common Intermediate Language (CIL) in un modulo nativo.
title: IDiaSymbol::get_isCVTCIL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isCVTCIL method
ms.assetid: 711b81fd-9549-44dc-9761-5eb862ed64c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f42afbcf3c6760e46ac009d2882dc0a56e2be9ec
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044150"
---
# <a name="idiasymbolget_iscvtcil"></a>IDiaSymbol::get_isCVTCIL
Recupera un flag che indica se il modulo è stato convertito da un modulo Common Intermediate Language (CIL) in un modulo nativo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isCVTCIL(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se il modulo è stato convertito da CIL a codice nativo; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Questa proprietà è disponibile dal `SymTagCompilandDetails` tipo di simbolo (vedere [CompilandDetails).](../../debugger/debug-interface-access/compilanddetails.md)

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
