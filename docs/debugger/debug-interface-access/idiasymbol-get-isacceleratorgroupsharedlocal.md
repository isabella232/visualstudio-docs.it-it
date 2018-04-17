---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 178ef0b2c1e5b24fb7a6af3e823111d875fd23cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa gruppo nel codice compilato per un tasto di scelta rapida di C++ AMP.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Un puntatore a un `BOOL` che indica se il simbolo corrisponde a una variabile locale condivisa gruppo nel codice compilato per un tasto di scelta rapida di C++ AMP. Se `TRUE`, `get_baseDataSlot` e `get_baseDataOffset` metodi possono essere utilizzati per ottenere le informazioni sul percorso di archiviazione per la variabile.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)