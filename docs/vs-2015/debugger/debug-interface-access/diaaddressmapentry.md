---
title: DiaAddressMapEntry | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa2824b7fbd10e7628e5c6b0a016615620933df9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756246"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Descrive una voce in una mappa di indirizzo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
struct DiaAddressMapEntry {   
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
  
1. Eseguire la ricerca della mappa per la voce `e`, con la più grande `rva` minore o uguale a `addrA`.  
  
2. Impostare `delta = addrA – e.rva`.  
  
3. Impostare `addrB = e.rvaTo + delta`.  
  
   Matrice di `DiaAddressMapEntry` strutture viene passato per il [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dia2.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)



