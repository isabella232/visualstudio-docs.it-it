---
title: 'IDiaEnumTables:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743757"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Recupera una tabella per mezzo di un indice o un nome.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Parametri
 `index`

in Indice o nome del [IDiaTable](../../debugger/debug-interface-access/idiatable.md) da recuperare. Se viene usata una variante Integer, deve essere compresa nell'intervallo da 0 a `count`-1, dove `count` è come restituito dal metodo [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .

 `table`

out Restituisce un oggetto [IDiaTable](../../debugger/debug-interface-access/idiatable.md) che rappresenta la tabella desiderata.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Se viene specificata una stringa Variant, la stringa assegna un nome a una tabella specifica. Il nome deve essere uno dei nomi di tabella come definito in [costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

## <a name="example"></a>Esempio

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Vedere anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)