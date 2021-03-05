---
description: Recupera un riferimento all'elemento padre lessicale del simbolo.
title: IDiaSymbol::get_lexicalParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d36147effa96d6c5a8ceb0b8f06a01cb0de5e455
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162005"
---
# <a name="idiasymbolget_lexicalparent"></a>IDiaSymbol::get_lexicalParent
Recupera un riferimento all'elemento padre lessicale del simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lexicalParent ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta l'elemento padre lessicale del simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 L'elemento padre lessicale di un simbolo è la funzione o il modulo contenitore. Ad esempio, l'elemento padre lessicale di un parametro di funzione o di una variabile locale è la funzione stessa mentre l'elemento padre lessicale della funzione è il modulo in cui è definito.

 I simboli possibili che possono essere visualizzati come elementi padre lessicali sono documentati nella [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
