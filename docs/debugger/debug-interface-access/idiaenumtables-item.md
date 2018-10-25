---
title: Idiaenumtables | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc95fe0f57eabbd933f8de842d842914948f3e4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819955"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Recupera una tabella tramite un indice o nome.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 [in] Indice o nome del [IDiaTable](../../debugger/debug-interface-access/idiatable.md) da recuperare. Se si usa una variante dell'integer, deve essere compreso nell'intervallo da 0 a `count`-1, dove `count` viene restituito dalle [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-get-count.md) (metodo).  
  
 `table`  
 [out] Restituisce un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) oggetto che rappresenta la tabella desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se viene specificata una variante di stringa, la stringa di nomi di una determinata tabella. Il nome deve essere uno dei nomi di tabella come definito in [costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Esempio  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Costanti (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)