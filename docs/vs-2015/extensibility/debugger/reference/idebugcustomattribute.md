---
title: IDebugCustomAttribute | Microsoft Docs
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
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7891e9be85fbac4f01a81e41dd36195f1ec41cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519906"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugCustomAttribute](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattribute).  
  
Questa interfaccia rappresenta un attributo personalizzato e fornisce il nome, padre e il tipo di classe dell'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia per supportare gli attributi personalizzati associati a un simbolo. Viene in genere implementato nel proprio oggetto.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [successivo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) restituisce questa interfaccia. Una chiamata ai [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) metodo restituisce il [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugCustomAttribute`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Ottiene il campo a cui è associato l'attributo corrente.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Ottiene il tipo di classe di attributo personalizzato.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Ottiene il nome dell'attributo personalizzato.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Ottiene le informazioni sugli attributi come un blob di byte.|  
  
## <a name="remarks"></a>Note  
 Un attributo personalizzato è una struttura per il linguaggio c# che fornisce metadati personalizzati associati a una determinata classe o metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

