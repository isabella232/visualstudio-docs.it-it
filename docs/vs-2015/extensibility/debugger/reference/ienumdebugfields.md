---
title: IEnumDebugFields | Microsoft Docs
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
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b56a0823ec0c2f02374e46fb8be61277da6adb88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517101"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IEnumDebugFields](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugfields).  
  
Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dal provider di simboli per specificare set di oggetti che implementano il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia. Si noti che questo non è un'enumerazione standard COM a causa della presenza del [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) (metodo).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene restituita da [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) e [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera il set successivo di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti dall'enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Ignora un determinato numero di voci.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Reimposta l'enumerazione per la prima voce.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera il numero di voci nell'enumerazione.|  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)

