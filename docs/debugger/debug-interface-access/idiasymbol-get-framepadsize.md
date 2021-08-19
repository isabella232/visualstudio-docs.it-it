---
description: Recupera le dimensioni aggiuntive del pad aggiunte a ogni funzione.
title: IDiaSymbol::get_framePadSize | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 052aa705c645ee7dc991f5311aa9d96f3b6a637d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052269"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol::get_framePadSize

Recupera le dimensioni aggiuntive del pad aggiunte a ogni funzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>Parametri

 `pPadSize`

[out] Restituisce le dimensioni aggiuntive del riempimento aggiunte a ogni funzione.

## <a name="return-value"></a>Valore restituito

 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti

Le dimensioni aggiuntive del pad vengono in genere usate da Modifica e continuazione.

Questo metodo è supportato a partire da Visual Studio 2019 versione 16.10 Preview 2.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
