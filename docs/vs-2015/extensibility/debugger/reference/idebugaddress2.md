---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 23fb27643a209e870165e521d63079a3b6c650eb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964721"
---
# <a name="idebugaddress2"></a>IDebugAddress2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia fornisce l'accesso all'ID del processo a cui appartiene l'oggetto il cui indirizzo è rappresentato da questa interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia nello stesso oggetto che implementa il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia. Questa interfaccia fornisce l'accesso all'ID del processo a cui appartiene l'oggetto correlato a questo indirizzo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Uso [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per ottenere questa interfaccia dalle [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable  
 Oltre ai metodi ereditati dal [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia, questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera l'ID del processo a cui appartiene l'oggetto rappresentato da questa interfaccia.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
