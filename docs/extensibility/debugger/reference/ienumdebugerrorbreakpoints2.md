---
title: Proprietà IEnumDebugErrorBreakpoints2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716889"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Questa interfaccia enumera i punti di interruzione di errore associati a un punto di interruzione in sospeso.

## <a name="syntax"></a>Sintassi

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del relativo supporto per i punti di interruzione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) per ottenere questa interfaccia che rappresenta un elenco di punti di interruzione che non possono essere associati o [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di punti di interruzione che non sono stati associati.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IEnumDebugErrorBreakpoints2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera un numero specificato di punti di interruzione di errore in una sequenza di enumerazione.|
|[Saltare](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Ignora un numero specificato di punti di interruzione di errore in una sequenza di enumerazione.|
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md) (Clona)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione di errore in un enumeratore.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia contiene un elenco di [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfacce, ognuno dei quali descrive un punto di interruzione che non è stato possibile associare e perché non è stato possibile associare. Visual Studio `IEnumDebugErrorBreakpoint2` usa l'interfaccia per aggiornare i punti di interruzione visualizzati nell'IDE.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
