---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576408"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Designa i tipi di thunk.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 `this`Thunk di regolazione.  
  
 THUNK_ORDINAL_VCALL  
 Thunk di chiamata virtuale.  
  
 THUNK_ORDINAL_PCODE  
 Thunk del codice P.  
  
 THUNK_ORDINAL_LOAD  
 Thunk di caricamento ritardato.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Thunk del trampolino incrementale (un thunk del trampolino viene usato per rimbalzare le chiamate da uno spazio di memoria a un altro).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Thunk del punto di ramo.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
