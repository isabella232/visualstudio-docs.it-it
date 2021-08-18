---
description: Questa interfaccia enumera DEBUG_PROPERTY_INFO strutture .
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 83e3f094763b19b712273563ce1446f07b1c1efd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152744"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Questa interfaccia enumera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture .

## <a name="syntax"></a>Sintassi

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare le informazioni per una determinata proprietà.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere questa interfaccia che rappresenta gli elementi figlio di una determinata proprietà. Chiamare [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) per ottenere questa interfaccia che rappresenta le proprietà di un stack frame.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugPropertyInfo2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera un numero specificato di strutture [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignora un numero specificato di strutture [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Ottiene il numero di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) in un enumeratore.|

## <a name="remarks"></a>Commenti
 In generale, una proprietà è una gerarchia di informazioni che può includere un nome, un valore, un indirizzo e un tipo, nonché qualsiasi altra informazione appropriata per l'oggetto o l'oggetto stack frame. Per [altri dettagli, vedere IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
