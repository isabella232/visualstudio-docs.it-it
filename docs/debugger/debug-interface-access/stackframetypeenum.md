---
title: StackFrameTypeEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fcf5e120e769b69c064306432c3026194eb0d851
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853935"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Specifica il tipo di frame dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
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