---
description: Recupera il simbolo che rappresenta il tipo per questo simbolo.
title: IDiaSymbol::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f0f6e86eaa78fd57d3cb62b1602111df1406f1bf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155628"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
Recupera il simbolo che rappresenta il tipo per questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametri
`pRetVal`

out Restituisce un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il tipo di questo simbolo.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
Per determinare il tipo di un simbolo, è necessario chiamare questo metodo ed esaminare l'oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) risultante. Si noti che è possibile che un simbolo non disponga di un tipo. Il nome di una struttura, ad esempio, non ha un tipo, ma potrebbe avere simboli figlio (usare il metodo [IDiaSymbol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) per esaminare tali elementi figlio).

## <a name="example"></a>Esempio

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
