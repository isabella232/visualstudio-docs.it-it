---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179198"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica il tipo di stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elementi  
 `FrameTypeFPO`  
 Puntatore al frame omesso; Informazioni sulla Polinesia disponibili.  
  
 `FrameTypeTrap`  
 Frame trap del kernel.  
  
 `FrameTypeTSS`  
 Frame trap del kernel.  
  
 `FrameTypeStandard`  
 Stack frame EBP standard.  
  
 `FrameTypeFrameData`  
 Puntatore al frame omesso; Informazioni sui dati dei frame disponibili.  
  
 `FrameTypeUnknown`  
 Frame senza informazioni di debug.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaStackFrame:: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
