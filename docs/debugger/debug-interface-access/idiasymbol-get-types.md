---
title: Get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94ff65cd9218ce26964d4dbb0da6fe2c3ffcae36
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868011"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Recupera una matrice di tipi specifici del compilatore per questo simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cTypes`  
 [in] Dimensione del buffer per contenere i dati.  
  
 `pcTypes`  
 [out] Restituisce il numero di tipi scritti, oppure, se il `types` parametro è `NULL`, quindi il numero totale dei tipi disponibili.  
  
 `types[]`  
 [out] Matrice che deve essere compilato con il [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) gli oggetti che rappresentano tutti i tipi per questo simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)