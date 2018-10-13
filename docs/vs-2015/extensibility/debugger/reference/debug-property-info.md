---
title: DEBUG_PROPERTY_INFO | Microsoft Docs
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
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 803583f97465cbd7b6e73c4f9a50f3f56d3617b0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202202"
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contiene informazioni su una proprietà di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>Membri  
 dwValidFields  
 Una combinazione di flag dal [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumerazione che specifica quali campi vengono compilati.  
  
 bstrFullName  
 Nome completo della proprietà.  
  
 bstrName  
 Il nome della proprietà all'interno di un contesto.  
  
 bstrType  
 Il tipo di proprietà come stringa formattata.  
  
 bstrValue  
 Il valore della proprietà come stringa formattata.  
  
 pProperty  
 Il [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto descritto da questa struttura.  
  
 dwAttrib  
 Una combinazione di flag dal [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumerazione che descrive gli attributi di questa proprietà.  
  
## <a name="remarks"></a>Note  
 Una proprietà è un oggetto di natura gerarchica che ha un nome, tipo e valore. Ad esempio, può descrivere una proprietà di variabili locali, parametri, controllare variabili e le espressioni e registri.  
  
 Questa struttura viene passata per il [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) in cui viene compilato nel metodo. Questa struttura viene anche restituita come parte di un elenco di questa struttura dal [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) interfaccia che, a sua volta, viene restituito da una chiamata ai [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) e [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

