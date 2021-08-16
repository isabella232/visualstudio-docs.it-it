---
description: Recupera una tabella tramite un indice o un nome.
title: IDiaEnumTables::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bddd0b00b5ad962424002f63302759349874de22e44db516ba244d523d16984f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392344"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Recupera una tabella tramite un indice o un nome.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Parametri
 `index`

[in] Indice o nome [dell'oggetto IDiaTable](../../debugger/debug-interface-access/idiatable.md) da recuperare. Se si usa una variante integer, deve essere compreso nell'intervallo da 0 a -1, dove è restituito dal metodo `count` `count` [IDiaEnumTables::get_Count.](../../debugger/debug-interface-access/idiaenumtables-get-count.md)

 `table`

[out] Restituisce un [oggetto IDiaTable](../../debugger/debug-interface-access/idiatable.md) che rappresenta la tabella desiderata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Se viene specificata una variante di stringa, la stringa nomi di una tabella specifica. Il nome deve essere uno dei nomi di tabella definiti in [Costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

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
