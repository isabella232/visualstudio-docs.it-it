---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e844438f5262b6a218a5feb355e78fc8a2cd1da
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005358"
---
# <a name="locationtype"></a>LocationType
Indica il tipo di informazioni di percorso contenute in un simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
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
 Informazioni sulla posizione non è disponibile.  
  
 `LocIsStatic`  
 Posizione è statica.  
  
 `LocIsTLS`  
 Si trova nell'archiviazione thread-local.  
  
 `LocIsRegRel`  
 Percorso è relativo al registro.  
  
 `LocIsThisRel`  
 Percorso è `this`-relativo.  
  
 `LocIsEnregistered`  
 Si trova in un registro di sistema.  
  
 `LocIsBitField`  
 Si trova in un campo di bit.  
  
 `LocIsSlot`  
 Trova uno slot di Microsoft Intermediate Language (MSIL).  
  
 `LocIsIlRel`  
 Percorso è relativo al codice MSIL.  
  
 `LocInMetaData`  
 Si trova nei metadati.  
  
 `LocIsConstant`  
 Si trova in un valore costante.  
  
 `LocTypeMax`  
 Il numero di tipi di percorso di questa enumerazione.  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà disponibili per il [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interfaccia dipendono dalla posizione del simbolo all'interno del file di immagine. Per altre informazioni, vedere [percorsi di simboli](../../debugger/debug-interface-access/symbol-locations.md).  
  
 I valori di questa enumerazione vengono restituiti da una chiamata per il [Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)