---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
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
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5169ff103b823067d64c58a3f6223220f67a3d52
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734218"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica le informazioni da recuperare su un contesto di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Membri  
 CIF_MODULEURL  
 Initialize/usare la `bstrModuleUrl` campo le [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struttura.  
  
 CIF_FUNCTION  
 Initialize/usare la `bstrFunction` campo il `CONTEXT_INFO` struttura.  
  
 CIF_FUNCTIONOFFSET  
 Initialize/usare la `posFunctionOffset` campo il `CONTEXT_INFO` struttura.  
  
 CIF_ADDRESS  
 Initialize/usare la `bstrAddress` campo il `CONTEXT_INFO` struttura.  
  
 CIF_ADDRESSOFFSET  
 Initialize/usare la `bstrAddressOffset` campo il `CONTEXT_INFO` struttura.  
  
 CIF_ALLFIELDS  
 Tutti i campi di inizializzazione/usare la `CONTEXT_INFO` struttura.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati un parametro per il [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metodo per indicare quali campi della [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struttura devono essere inizializzate.  
  
 Questi flag vengono usanti anche per indicare quali campi del `CONTEXT_INFO` struttura siano usati e validi quando viene restituita la struttura.  
  
 Questi valori possono essere combinati con un OR bit per bit.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)

