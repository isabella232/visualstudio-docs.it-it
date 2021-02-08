---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf9cd3cb82e2b14811a8ec52a651248e2990ae27
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840366"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Questa interfaccia fornisce le porte al gestore di debug della sessione (SDM).

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un fornitore di porte.

## <a name="notes-for-callers"></a>Note per i chiamanti
Una chiamata a `CoCreateInstance` con un fornitore di porte `GUID` restituisce questa interfaccia (questo è il modo tipico per ottenere questa interfaccia). Ad esempio:

```cpp
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

Una chiamata a [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) restituisce questa interfaccia, che rappresenta il fornitore della porta corrente usato da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) restituisce questa interfaccia, che rappresenta il fornitore della porta che ha creato la porta.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) rappresenta un elenco di `IDebugPortSupplier` interfacce (l' `IEnumDebugPortSuppliers` interfaccia viene ottenuta da [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), che rappresenta tutti i fornitori di porte registrati con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

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

## <a name="remarks"></a>Commenti
Un fornitore di porte può identificare se stesso in base al nome e all'ID, aggiungere e rimuovere porte ed enumerare tutte le porte fornite dal fornitore della porta.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
