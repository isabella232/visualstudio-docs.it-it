---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 756a1b9fde9c85ca914b00924cb13191859be78e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952301"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Definisce i tipi di thunk.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elementi  
 THUNK_ORDINAL_NOTYPE  
 Thunk standard.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Oggetto `this` thunk DS.  
  
 THUNK_ORDINAL_VCALL  
 Thunk chiamata virtuale.  
  
 THUNK_ORDINAL_PCODE  
 Thunk P-code.  
  
 THUNK_ORDINAL_LOAD  
 Thunk carico ritardo.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Thunk trampoline incrementale (un thunk trampoline viene usato a oscillare in chiamate dallo spazio di memoria a un altro).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Thunk trampoline punto di ramo.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono restituiti da una chiamata per il [Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)