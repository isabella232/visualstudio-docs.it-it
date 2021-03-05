---
description: Recupera il flag che indica se i simboli privati sono stati rimossi dal file di simboli.
title: IDiaSymbol::get_isStripped | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStripped method
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa52f28bf31a8bd13d9f45ce8554696c91961340
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162061"
---
# <a name="idiasymbolget_isstripped"></a>IDiaSymbol::get_isStripped
Recupera il flag che indica se i simboli privati sono stati rimossi dal file di simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isStripped(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

out Restituisce `TRUE` se i simboli privati sono stati rimossi dal file di simboli; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Questa proprietà è disponibile dal `SymTagExe` tipo di simbolo (vedere [exe](../../debugger/debug-interface-access/exe.md)).

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
