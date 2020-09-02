---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d9c3f8b45affd192d4109db08454345dcd0814
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188230"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia fornisce le porte al gestore di debug della sessione (SDM).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un fornitore di porte.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a `CoCreateInstance` con un fornitore di porte `GUID` restituisce questa interfaccia (questo è il modo tipico per ottenere questa interfaccia). Ad esempio:  
  
```cpp#  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Una chiamata a [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) restituisce questa interfaccia, che rappresenta il fornitore della porta corrente usato da [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) restituisce questa interfaccia, che rappresenta il fornitore della porta che ha creato la porta.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) rappresenta un elenco di `IDebugPortSupplier` interfacce (l' `IEnumDebugPortSuppliers` interfaccia viene ottenuta da [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), che rappresenta tutti i fornitori di porte registrati con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ).  
  
 Un motore di debug non interagisce in genere con un fornitore di porte.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugPortSupplier2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ottiene il nome del fornitore della porta.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Ottiene l'identificatore del fornitore della porta.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Ottiene una porta da un fornitore di porte.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera le porte già esistenti.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Verifica che un fornitore di porte supporti l'aggiunta di nuove porte.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Aggiunge una porta.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Rimuove una porta.|  
  
## <a name="remarks"></a>Osservazioni  
 Un fornitore di porte può identificare se stesso in base al nome e all'ID, aggiungere e rimuovere porte ed enumerare tutte le porte fornite dal fornitore della porta.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
