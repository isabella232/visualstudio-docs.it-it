---
title: IDiaSymbol::get_intro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 153daa1f43ba4945a5eb32aea82c5d58ff57c5f6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836800"
---
# <a name="idiasymbolgetintro"></a>IDiaSymbol::get_intro
Recupera un flag che specifica se la funzione è un'introduzione alle funzioni virtuali.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
`pRetVal`

[out] Restituisce `TRUE` se la funzione è intro virtuale; in caso contrario, restituisce `FALSE`.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.

## <a name="example"></a>Esempio

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Entrambe `A::f1` e `B::f1` sono funzioni virtuali, ma `A::f1` è virtuale introduttivo.

## <a name="requirements"></a>Requisiti

|Requisito|DESCRIZIONE|
|-----------------|-----------------|
|Intestazione:|DIA2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
