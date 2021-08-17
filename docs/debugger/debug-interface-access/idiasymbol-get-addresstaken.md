---
description: Recupera un flag che indica se un altro simbolo fa riferimento all'indirizzo di questo simbolo.
title: IDiaSymbol::get_addressTaken | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 132fa45ef2ab2adb4a79283742bf9a566aa7a59e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052314"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
Recupera un flag che indica se un altro simbolo fa riferimento all'indirizzo di questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se un altro simbolo fa riferimento a questo indirizzo; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="example"></a>Esempio
 Nell'esempio seguente fa `B` riferimento a `A` . Di conseguenza, il `A` metodo del simbolo restituisce `get_addressTaken` `TRUE` .

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
