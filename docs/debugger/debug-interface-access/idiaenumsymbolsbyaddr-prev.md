---
title: IDiaEnumSymbolsByAddr::Prev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81700f73b7a1730a4f74f5340d5928b3662db3b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933491"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Recupera i simboli precedenti nell'ordine in base all'indirizzo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di simboli nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Matrice che deve essere compilata con [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) gli oggetti che rappresentano i simboli desiderati.  
  
 pceltFetched  
 [out] Restituisce il numero di simboli nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti simboli precedenti. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo aggiorna la posizione di enumeratore per il numero di elementi recuperati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)