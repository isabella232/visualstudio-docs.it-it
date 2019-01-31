---
title: Idiaenumtables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e1cad345d099c9f5f8ecd870bcd80de7c886a55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977577"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Recupera un determinato numero di tabelle nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di tabelle nell'enumeratore deve essere recuperato.  
  
 `rgelt`  
 [out] Matrice che deve essere compilato con il [IDiaTable](../../debugger/debug-interface-access/idiatable.md) gli oggetti che rappresentano le tabelle desiderate.  
  
 `pceltFetched`  
 [out] Restituisce il numero di tabelle nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non siano presenti altre tabelle. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)