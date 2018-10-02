---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
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
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 999b9af039513782439ca89826f54c94da79546f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519223"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DEBUGPROP_INFO_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debugprop-info-flags).  
  
Specifica le informazioni da recuperare un oggetto di proprietà di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 DEBUGPROP_INFO_FULLNAME  
 Initialize/usare la `bstrFullName` campo.  
  
 DEBUGPROP_INFO_NAME  
 Initialize/usare la `bstrName` campo.  
  
 DEBUGPROP_INFO_TYPE  
 Initialize/usare la `bstrType` campo.  
  
 DEBUGPROP_INFO_VALUE  
 Initialize/usare la `bstrValue` campo.  
  
 DEBUGPROP_INFO_ATTRIB  
 Initialize/usare la `dwAttrib` campo.  
  
 DEBUGPROP_INFO_PROP,  
 Initialize/usare la `pProperty` campo che contiene un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Specifica che il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Deprecato.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Non restituiscono alcun valore beautified o i membri (vale a dire non formattare i valori).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Non restituisce alcun valore sintetizzati speciali (ad esempio, non chiamare `ToString()` su un oggetto per produrre un valore).  
  
 DEBUGPROP_INFO_NONE  
 Specifica che non sono impostati flag.  
  
 DEBUGPROP_INFO_STANDARD  
 Initialize/usare la `dwAttrib`, `bstrName`, `bstrType`, e `bstrValue` campi.  
  
 DEBUGPROP_INFO_All  
 Indica una maschera di tutti i flag.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati per il [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), e [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metodi per indicare quali campi devono essere inizializzate di [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura.  
  
 Questi valori vengono utilizzati anche per il `dwFields` membro del `DEBUG_PROPERTY_INFO` struttura per indicare quali campi della struttura sono usati e validi quando viene restituita la struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)

