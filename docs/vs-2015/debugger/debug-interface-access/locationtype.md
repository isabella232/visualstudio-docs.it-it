---
title: LocationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154195"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica il tipo di informazioni sulla posizione contenute in un simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Elementi  
 `LocIsNull`  
 Le informazioni sulla posizione non sono disponibili.  
  
 `LocIsStatic`  
 Il percorso è statico.  
  
 `LocIsTLS`  
 Il percorso si trova nell'archiviazione thread-local.  
  
 `LocIsRegRel`  
 Il percorso è relativo al registro.  
  
 `LocIsThisRel`  
 Il percorso è `this` relativo.  
  
 `LocIsEnregistered`  
 Il percorso si trova in un registro.  
  
 `LocIsBitField`  
 Il percorso si trova in un campo di bit.  
  
 `LocIsSlot`  
 Location è uno slot MSIL (Microsoft Intermediate Language).  
  
 `LocIsIlRel`  
 Il percorso è relativo a MSIL.  
  
 `LocInMetaData`  
 Il percorso è nei metadati.  
  
 `LocIsConstant`  
 Il percorso è in un valore costante.  
  
 `LocTypeMax`  
 Numero di tipi di posizione in questa enumerazione.  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà disponibili per l'interfaccia [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dipendono dalla posizione del simbolo all'interno del file di immagine. Per ulteriori informazioni, vedere [posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md).  
  
 I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)
