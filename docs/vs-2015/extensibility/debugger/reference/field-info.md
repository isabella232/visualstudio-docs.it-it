---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e18e906cbc65ea811e765553a8d2711b3e4eb0f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423738"
---
# <a name="fieldinfo"></a>FIELD_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura descrive una variabile locale, parametro o altri campi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Membri  
 dwFields  
 Una combinazione di flag dal [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumerazione che specifica i membri che vengono compilati.  
  
 bstrFullName  
 Il nome completo del campo.  
  
 bstrName  
 Il nome breve del campo.  
  
 bstrType  
 Il tipo del campo.  
  
 dwModifiers  
 Una combinazione di flag dal [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumerazione che descrive il campo.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) in cui viene compilato nel metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
