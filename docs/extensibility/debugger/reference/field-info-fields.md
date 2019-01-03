---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e48ac549001ed8a6ef363540cf50affb0e7b605
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902506"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Specifica le informazioni da recuperare su un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Membri  
 FIF_FULLNAME  
 Initialize/usare la `bstrFullName` campo le [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura.  
  
 FIF_NAME  
 Initialize/usare la `bstrName` campo il `FIELD_INFO` struttura.  
  
 FIF_TYPE  
 Initialize/usare la `bstrType` campo il `FIELD_INFO` struttura.  
  
 FIF_MODIFIERS  
 Initialize/usare la `bstrModifiers` campo il `FIELD_INFO` struttura.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati anche come argomento per il [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodo per specificare quali campi della [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura devono essere inizializzate.  
  
 Questi valori vengono anche utilizzati nel `dwFields` membro del `FIELD_INFO` struttura per indicare quali campi vengono usati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)