---
title: Interfaccia metodo ienumjsstackframes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572023"
---
# <a name="ienumjsstackframes-interface"></a>Interfaccia IEnumJsStackFrames
Implementato dal debugger per fornire la rimozione dello stack a jscript9diag. dll per JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Name|Descrizione|  
|----------|-----------------|  
|[Metodo IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Ottiene il numero di frame specificato.|  
|[Metodo IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Reimposta la stack frame sulla posizione prima del primo elemento.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)