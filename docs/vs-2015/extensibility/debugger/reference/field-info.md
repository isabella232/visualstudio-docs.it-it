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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423738"
---
# <a name="field_info"></a>FIELD_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura descrive una variabile locale, un parametro o un altro campo.  
  
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
 Combinazione di flag dell'enumerazione [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) che specifica i membri che vengono compilati.  
  
 bstrFullName  
 Nome completo del campo.  
  
 bstrName  
 Nome breve del campo.  
  
 bstrType  
 Tipo del campo.  
  
 dwModifiers  
 Combinazione di flag dell'enumerazione [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) che descrive il campo.  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene passata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) dove viene compilata.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
