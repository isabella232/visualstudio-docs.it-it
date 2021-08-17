---
description: Recupera un flag che specifica se la funzione è una funzione virtuale di introduzione.
title: IDiaSymbol::get_intro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9d0db207315cf2bc8dafda9dedd533cacdef261e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031268"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Recupera un flag che specifica se la funzione è una funzione virtuale di introduzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
`pRetVal`

[out] Restituisce `TRUE` se la funzione è intro virtual; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o il `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="example"></a>Esempio

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Sia `A::f1` che sono funzioni `B::f1` virtuali, ma sono virtuali `A::f1` introduttivi.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
