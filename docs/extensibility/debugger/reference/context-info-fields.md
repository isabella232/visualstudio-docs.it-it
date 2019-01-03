---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 532a2f309af612fb74a2f810b7fe445b79f813fc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847960"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Specifica le informazioni da recuperare su un contesto di memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
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
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)