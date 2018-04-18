---
title: DiaAddressMapEntry | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc13e8813c0e1bddd1f6cb9abd3d70b26eb5a8e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Descrive una voce nella mappa di un indirizzo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elementi  
 `rva`  
 Un indirizzo virtuale relativo (RVA) nell'immagine A.  
  
 `rvaTo`  
 L'indirizzo virtuale relativo `rva` viene mappato a nell'immagine B.  
  
## <a name="remarks"></a>Note  
 Mappa di un indirizzo fornisce una conversione dal layout di un'immagine (A) a un altro (B). Matrice di `DiaAddressMapEntry` strutture ordinate `rva` definisce un mapping di indirizzi.  
  
 Per convertire un indirizzo, `addrA`, nell'immagine A un indirizzo, `addrB`, nell'immagine B, eseguire la procedura seguente:  
  
1.  Cercare la mappa per la voce, `e`, con il valore massimo `rva` minore o uguale a `addrA`.  
  
2.  Set `delta = addrA - e.rva`.  
  
3.  Set `addrB = e.rvaTo + delta`.  
  
 Matrice di `DiaAddressMapEntry` strutture viene passato per il [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)