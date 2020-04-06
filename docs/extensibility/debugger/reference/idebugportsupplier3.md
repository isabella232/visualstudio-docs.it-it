---
title: Proprietà IDebugPortSupplier3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724432"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Questa interfaccia consente a un chiamante di determinare se un fornitore di porte può mantenere le porte (scrivendole su disco) tra le chiamate del debugger e quindi ottenere un elenco di tali porte mantenute.

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porta personalizzato implementa questa interfaccia per supportare la persistenza o il salvataggio delle informazioni sulla porta su disco. Questa interfaccia deve essere implementata sullo stesso oggetto di [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) `IDebugPortSupplier2` sull'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi ereditati dal IDebugPortSupplier2 interfaccia, questa interfaccia supporta quanto segue:In addition to the methods inherited from the [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface, this interface supports the following:

|Metodo|Descrizione|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Restituisce un valore che indica se il fornitore della porta può mantenere le porte (scrivendole su disco) tra le chiamate del debugger.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Restituisce un oggetto che può essere utilizzato per enumerare tutte le porte scritte su disco da questo fornitore di porte.|

## <a name="remarks"></a>Osservazioni
 Se un fornitore di porte può rendere persistenti le porte tra le chiamate, deve implementare questa interfaccia. Le porte devono essere caricate quando viene creata un'istanza del fornitore della porta e scritte su disco quando il fornitore della porta viene eliminato.

 Un motore di debug in genere non interagisce con un fornitore di porta e non avrà alcun utilizzo per questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
