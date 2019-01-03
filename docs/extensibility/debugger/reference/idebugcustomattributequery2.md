---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5c71c8a8820a76eb0f3784aaf899f05f48a76e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836374"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Determina l'esistenza di un attributo personalizzato per questo campo e, se presente, restituisce le informazioni sugli attributi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia nello stesso oggetto che implementa [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) per supportare gli attributi personalizzati.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Uso [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dalle [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi del **IDebugCustomAttributeQuery** interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina l'esistenza di un attributo personalizzato in base al nome.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ottiene le informazioni sugli attributi per l'attributo personalizzato specificato.|  
  
 Oltre al **IDebugCustomAttributeQuery** metodi, `IDebugCustomAttributeQuery2` implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ottiene un enumeratore per tutti gli attributi personalizzati collegati a questo campo.|  
  
## <a name="remarks"></a>Note  
 Il [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) metodo può restituire un enumeratore per tutti gli attributi personalizzati definiti per questo campo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)