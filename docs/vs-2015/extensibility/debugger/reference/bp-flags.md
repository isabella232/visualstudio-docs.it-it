---
title: BP_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6feb965c564e74dbb026a66a964d233b3ed75fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517449"
---
# <a name="bpflags"></a>BP_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [BP_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-flags).  
  
Fornisce flag opzionale che può essere usato per specificare informazioni aggiuntive durante l'impostazione di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Membri  
 BP_FLAG_NONE  
 Non specifica alcun flag per il punto di interruzione.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Specifica che il motore di debug (DE) deve eseguire il mapping del punto di interruzione usando la posizione del documento. Ciò si applica solo ai punti di interruzione impostati nei file di origine orientata ai servizi script, ad esempio le pagine ASP (Active Server).  
  
 BP_FLAG_DONT_STOP  
 Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug in definitiva non deve arrestare presenti (vale a dire, un' [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) oggetto dell'evento non deve essere inviato). Questo flag è progettato per essere usato principalmente con i punti di analisi.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `dwFlags` membro della [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
