---
description: Questa interfaccia consente a un chiamante di determinare se un fornitore di porte può mantenere le porte (scrivendole su disco) tra le chiamate del debugger e quindi ottenere un elenco di tali porte mantenute.
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 84dc23cf1c750d539d043b1993490a523c70ebaaacf04cc44c8702d8383278ad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416755"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Questa interfaccia consente a un chiamante di determinare se un fornitore di porte può mantenere le porte (scrivendole su disco) tra le chiamate del debugger e quindi ottenere un elenco di tali porte mantenute.

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per supportare la persistenza o il salvataggio delle informazioni sulla porta su disco. Questa interfaccia deve essere implementata nello stesso oggetto [dell'interfaccia IDebugPortSupplier2.](../../../extensibility/debugger/reference/idebugportsupplier2.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) `IDebugPortSupplier2` sull'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi ereditati [dall'interfaccia IDebugPortSupplier2,](../../../extensibility/debugger/reference/idebugportsupplier2.md) questa interfaccia supporta quanto segue:

|Metodo|Descrizione|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Restituisce un valore che indica se il fornitore della porta può rendere persistenti le porte (scrivendole su disco) tra le chiamate del debugger.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Restituisce un oggetto che può essere utilizzato per enumerare tutte le porte scritte su disco da questo fornitore di porte.|

## <a name="remarks"></a>Commenti
 Se un fornitore di porte può rendere persistenti le porte tra le chiamate, deve implementare questa interfaccia. Le porte devono essere caricate quando viene creata un'istanza del fornitore della porta e scritte su disco quando il fornitore della porta viene eliminato.

 Un motore di debug in genere non interagisce con un fornitore di porte e non avrà alcun uso per questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
