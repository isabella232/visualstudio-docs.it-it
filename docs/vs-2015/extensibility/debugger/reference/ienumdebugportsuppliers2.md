---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
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
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d148ba120f4dd70f271e36933ad2395517469ad1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736234"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia enumera i fornitori di porte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare un elenco di fornitori di porte.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) per ottenere un elenco di fornitori di porte.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPortSuppliers2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Recupera un determinato numero di fornitori di porte in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignora un determinato numero di fornitori di porte in una sequenza di enumerazione.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Ottiene il numero di fornitori di porte in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Un motore di debug non è in genere necessario ottenere questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)

