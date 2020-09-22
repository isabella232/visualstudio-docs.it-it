---
title: CV_call_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839795"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica la convenzione di chiamata per una funzione.  
  
> [!NOTE]
> Solo i valori di enumerazione più comuni sono documentati qui. L'enumerazione complete è disponibile nel file di intestazione cvconst. h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elementi  
 CV_CALL_NEAR_C  
 Specifica una convenzione di chiamata di funzione utilizzando un push vicino da destra a sinistra. La funzione chiamante Cancella lo stack.  
  
 CV_CALL_NEAR_FAST  
 Specifica una convenzione di chiamata di funzione utilizzando un push vicino da sinistra a destra con registri. La funzione chiamata utilizza la somma dei byte del parametro per cancellare lo stack.  
  
 CV_CALL_NEAR_STD  
 Specifica una convenzione di chiamata di funzione utilizzando una chiamata near standard (push da destra a sinistra).  
  
 CV_CALL_NEAR_SYS  
 Specifica una convenzione di chiamata di funzione utilizzando una chiamata di sistema near.  
  
 CV_CALL_THISCALL  
 Specifica una convenzione di chiamata di funzione utilizzando `this` Call ( `this` puntatore passato nel registro).  
  
 CV_CALL_CLRCALL  
 Specifica una convenzione di chiamata di funzione utilizzata da Common Language Runtime (CLR), nota anche come convenzione di chiamata del codice gestito.  
  
## <a name="remarks"></a>Commenti  
 I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
