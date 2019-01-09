---
title: Interfaccia IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c26470e02f6c7e5d8911df7e743bce0cb0e560bb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087880"
---
# <a name="ienumjsstackframes-interface"></a>Interfaccia IEnumJsStackFrames
Implementata dal debugger per fornire dello stack di rimozione in jscript9diag.dll per JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Ottiene il numero di frame specificato.|  
|[Metodo IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Reimposta lo stack frame alla posizione prima del primo elemento.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)