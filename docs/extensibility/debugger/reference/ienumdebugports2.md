---
description: Questa interfaccia enumera le porte di un fornitore di computer o porte.
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 243fcf1476f2f278ebed550805fcdfc9cf82d03300a1df70ad2c1c833ac3cdc8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121291688"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Questa interfaccia enumera le porte di un fornitore di computer o porte.

## <a name="syntax"></a>Sintassi

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un elenco di porte create dal fornitore. Visual Studio implementa questa interfaccia a supporto del proprio fornitore di porte.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumPorts per](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) ottenere questa interfaccia che rappresenta un elenco di porte create dal fornitore della porta. Chiamare [EnumPersistedPorts per](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) ottenere questa interfaccia che rappresenta un elenco di porte salvate su disco.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugPorts2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Recupera un numero specificato di porte in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Ignora un numero specificato di porte in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Ottiene il numero di porte in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio usa questa interfaccia per popolare un elenco di porte usate per la connessione ai processi.

 Un motore di debug in genere non usa questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
