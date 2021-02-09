---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3f1ae87cc9d0926d7afc22d819dddf672a89afd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883805"
---
# <a name="idebugreference2"></a>IDebugReference2
Questa interfaccia rappresenta un riferimento a una proprietà stack frame o a un'altra proprietà.

> [!NOTE]
> `IDebugReference2` è riservata per utilizzi futuri e tutti i relativi metodi devono restituire `E_NOTIMPL` .

## <a name="syntax"></a>Sintassi

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per rappresentare un riferimento a un particolare tipo di valore. Ad esempio, il valore può essere un valore numerico come risultato della valutazione di un'espressione, un contesto di memoria usato per la visualizzazione della memoria o un elenco di registri e i relativi valori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) per ottenere questa interfaccia. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) e [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) restituiscono anche questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugReference2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ottiene la struttura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) che descrive il riferimento.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Imposta il valore di questo riferimento da una stringa.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Imposta il valore di questo riferimento da un altro riferimento.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera gli elementi figlio di questo riferimento.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ottiene l'elemento padre di questo riferimento.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ottiene il riferimento più derivato del riferimento.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ottiene i byte di memoria a cui si riferisce il riferimento.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ottiene un contesto di memoria per questo riferimento.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ottiene la dimensione, in byte, del riferimento.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Imposta questo tipo di riferimento.|
|[Confronta](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Confronta questo riferimento con un altro.|

## <a name="remarks"></a>Commenti

> [!NOTE]
> Questo utilizzo di "Property" non deve essere confuso con quello che significa una variabile membro di una classe, sebbene `IDebugReference2` possa rappresentare tale entità.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rappresenta una proprietà, mentre `IDebugReference2` rappresenta un riferimento a una proprietà, in genere un riferimento a un oggetto nel programma di cui è in corso il debug.

 La differenza principale tra una proprietà e un riferimento è che una proprietà fa riferimento a un'istanza denominata di un oggetto, mentre un riferimento si riferisce a un'istanza senza nome. Una proprietà, ad esempio, può fare riferimento a un oggetto nell'heap del programma da `"a.b"` . Un'altra proprietà può fare riferimento allo stesso oggetto di `"c.d"` . Per fare riferimento a questa proprietà, è necessario che `"a.b"` o `"c.d"` siano nell'ambito. Un riferimento allo stesso oggetto è senza nome; è possibile fare riferimento all'oggetto purché la memoria per l'oggetto sia valida.

 Un' `IDebugProperty2` interfaccia può essere considerata come un valore con un nome, un tipo e un indirizzo. Un oggetto `IDebugReference2` , d'altra parte, può essere considerato come un tipo e un indirizzo.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
