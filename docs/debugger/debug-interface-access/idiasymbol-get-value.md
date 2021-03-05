---
description: Recupera il valore di una costante.
title: IDiaSymbol::get_value | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_value method
ms.assetid: 2e40174a-2a61-4e5f-bb32-9e0ceec2178a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 680ddd3dd90538e3e37991e890b61bc74220c8a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161788"
---
# <a name="idiasymbolget_value"></a>IDiaSymbol::get_value
Recupera il valore di una costante.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_value (
    VARIANT* pRetVal
);
```

#### <a name="parameters"></a>Parametri
`pRetVal`

[in, out] `VARIANT` Oggetto compilato con il valore di una costante.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
La variante fornita deve essere inizializzata prima di essere passata a questo metodo. Per ulteriori informazioni, vedere l'esempio.

## <a name="example"></a>Esempio

```C++
void ProcessValue(IDiaSymbol *pSymbol)
{
    VARIANT value;
    value.vt = VT_EMPTY;    // Initialize variant for use.
    if (pSymbol->get_value(&value) == S_OK)
    {
        // Do something with value.
    }
}

//----------------------------------------------------
// Alternate approach
void ProcessValue2(IDiaSymbol *pSymbol)
{
    CComVariant value;
    if (pSymbol->get_value(&value) == S_OK)
    {
        // Do something with value
    }
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
