---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3150cc591c77d1ab3abc31ed9b07062d094d3d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973096"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Fornisce un mapping di indirizzi per supportare le traduzioni di layout di immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Il numero di elementi nel `data` parametro.  
  
 `data[]`  
 [in] Matrice di [struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) strutture che definiscono il mapping per la conversione.  
  
 `imagetoSymbols`  
 [in] `TRUE` se il `data` parametro definisce una mappa dal layout dell'immagine di nuovo il layout originale (come descritto per i simboli di debug). `FALSE` Se `data` è una mappa per il nuovo layout dell'immagine ricavato il layout originale.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, il DIA recupera indirizzo traduzione mappe dal file di database (con estensione pdb) del programma. Se questi valori non sono presenti, il [Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) viene chiamato due volte, una volta con i `imagetoSymbols` parametro impostato su `TRUE` e una volta con il `imagetoSymbols` parametro impostato su `FALSE`. Conversioni di mapping di indirizzi non possono essere abilitate usando il [Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metodo a meno che non vengono fornite entrambe le mappe di traduzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)