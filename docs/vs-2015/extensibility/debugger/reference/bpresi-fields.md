---
title: BPRESI_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 760e33f6b2f99450e4ffc69461236376eb70320f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286624"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica le informazioni da recuperare sulla corretta risoluzione di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 BPRESI_BPRESLOCATION  
 Initialize/usare la `bpResLocation` campo (punto di interruzione risoluzione percorso) della finestra di [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura.  
  
 BPRESI_PROGRAM  
 Initialize/usare la `pProgram` campo il `BP_RESOLUTION_INFO` struttura.  
  
 BPRESI_THREAD  
 Initialize/usare la `pThread` campo il `BP_RESOLUTION_INFO` struttura.  
  
 BPRESI_ALLFIELDS  
 Specifica tutti i campi.  
  
## <a name="remarks"></a>Note  
 Passato per il [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metodo per indicare quali campi della [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura devono essere inizializzate.  
  
 Questi flag vengono usanti anche per indicare quali campi del `BP_RESOLUTION_INFO` struttura siano usati e validi quando viene restituita tale struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

