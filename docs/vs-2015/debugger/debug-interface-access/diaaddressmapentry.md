---
title: DiaAddressMapEntry | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6d5075917c49be66d030846cdc186b0fa5e50a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530868"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DiaAddressMapEntry](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/diaaddressmapentry).  
  
Descrive una voce in una mappa di indirizzo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elementi  
 `rva`  
 Un indirizzo virtuale relativo (RVA) nell'immagine A.  
  
 `rvaTo`  
 L'indirizzo virtuale relativo `rva` viene mappato a nella figura B.  
  
## <a name="remarks"></a>Note  
 Una mappa indirizzo fornisce una conversione dal layout di un'immagine (A) in un'altra (B). Matrice di `DiaAddressMapEntry` strutture vengono ordinate `rva` definisce un mapping di indirizzi.  
  
 Per convertire un indirizzo `addrA`, nell'immagine A un indirizzo, `addrB`, nella figura B, eseguire la procedura seguente:  
  
1.  Eseguire la ricerca della mappa per la voce `e`, con la più grande `rva` minore o uguale a `addrA`.  
  
2.  Impostare `delta = addrA – e.rva`.  
  
3.  Impostare `addrB = e.rvaTo + delta`.  
  
 Matrice di `DiaAddressMapEntry` strutture viene passato per il [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)



