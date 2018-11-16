---
title: StackFrameTypeEnum | Microsoft Docs
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
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de80fd054459556e273427b666175751ced203fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740374"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica il tipo di frame dello stack.  
  
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
 Puntatore ai frame omessi. Info FPO disponibile.  
  
 `FrameTypeTrap`  
 Frame Trap kernel.  
  
 `FrameTypeTSS`  
 Frame Trap kernel.  
  
 `FrameTypeStandard`  
 Frame dello stack EBP standard.  
  
 `FrameTypeFrameData`  
 Puntatore ai frame omessi. Informazioni sui dati di intervallo disponibile.  
  
 `FrameTypeUnknown`  
 Frame che non ha le informazioni di debug.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono restituiti da una chiamata per il [Idiastackframe](../../debugger/debug-interface-access/idiastackframe-get-type.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



