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
ms.openlocfilehash: ca14e6236fc7e12ea259b97f7f2ddb69fe052f55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692834"
---
# <a name="idebugaddress2"></a>IDebugAddress2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia consente di accedere all'ID del processo a cui appartiene l'oggetto il cui indirizzo è rappresentato da questa interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa l'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Questa interfaccia consente di accedere all'ID del processo a cui appartiene l'oggetto correlato a questo indirizzo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Usare [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per ottenere questa interfaccia dall'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable  
 Oltre ai metodi ereditati dall'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera l'ID del processo a cui appartiene l'oggetto rappresentato da questa interfaccia.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
