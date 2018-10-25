---
title: CANSTOP_REASON | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4129839094b7f5cf9907f6b92fa11fe1847f5806
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938812"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Utilizzato per determinare se un programma può arrestare l'esecuzione dopo aver raggiunto un punto particolare nell'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Membri  
 CANSTOP_ENTRYPOINT  
 Specifica il punto di ingresso del programma specificato.  
  
 CANSTOP_STEPIN  
 Specifica l'esecuzione di una funzione.  
  
## <a name="remarks"></a>Note  
 Passato come argomento per il [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodo per confermare con sessione di Debug Manager (SDM) se è corretto arrestare dopo aver raggiunto il punto di ingresso del programma o dopo l'esecuzione di una funzione o metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)