---
description: Questa interfaccia fornisce porte alla gestione del debug di sessione (SDM).
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ded700cb5f9e6c7ff725f0b7049842d3e308b014
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088107"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Questa interfaccia fornisce porte alla gestione del debug di sessione (SDM).

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un fornitore di porte.

## <a name="notes-for-callers"></a>Note per i chiamanti
Una chiamata a con un fornitore di porte restituisce questa interfaccia (questo è il modo `CoCreateInstance` tipico per ottenere questa `GUID` interfaccia). Esempio:

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

Una chiamata a [GetPortSupplier restituisce](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) questa interfaccia, che rappresenta il fornitore di porta corrente usato da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) restituisce questa interfaccia, che rappresenta il fornitore della porta che ha creato la porta.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) rappresenta un elenco di interfacce (l'interfaccia viene ottenuta da `IDebugPortSupplier` `IEnumDebugPortSuppliers` [EnumPortSuppliers,](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)che rappresenta tutti i fornitori di porte registrati con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

Un motore di debug in genere non interagisce con un fornitore di porte.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDebugPortSupplier2` .

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
Un fornitore di porte può identificarsi in base al nome e all'ID, aggiungere e rimuovere porte ed enumerare tutte le porte fornite dal fornitore della porta.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
