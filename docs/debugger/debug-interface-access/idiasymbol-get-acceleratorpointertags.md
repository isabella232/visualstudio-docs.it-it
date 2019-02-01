---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f94ea23c1a6afd16f57a2ffb9944cf8a7ded5c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019541"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Restituisce tutti i valori di tag puntatore tasti di scelta rapida che corrispondono a una funzione di stub di tasti di scelta rapida AMP C++.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cnt`  
 [in] Le dimensioni della matrice di output `pPointerTags`.  
  
 `pcnt`  
 [out] Il conteggio dei tag di puntatore tasti di scelta rapida nella funzione di stub di tasti di scelta rapida AMP C++.  
  
 `pPointerTags`  
 [out] Oggetto `DWORD` puntatore di una matrice che viene riempito con i valori di tag acceleratore puntatore della funzione di stub di tasti di scelta rapida AMP C++.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato su un `IDiaSymbol` interfaccia che corrisponde a una funzione di stub di tasti di scelta rapida AMP C++.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)