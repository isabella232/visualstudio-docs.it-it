---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d34b7a915f2eb2bd1ddf9440c543d652de8eb892
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713334"
---
# <a name="idebugreference2"></a>IDebugReference2
Questa interfaccia rappresenta un riferimento a una proprietà frame dello stack o un'altra proprietà.

> [!NOTE]
>  `IDebugReference2` è riservato per utilizzi futuri e tutti i relativi metodi devono restituire `E_NOTIMPL`.

## <a name="syntax"></a>Sintassi

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 La Germania implementa questa interfaccia per rappresentare un riferimento a un particolare tipo di valore. Ad esempio, il valore può essere un valore numerico come risultato di valutazione di un'espressione, un contesto di memoria utilizzata per la visualizzazione di memoria o un elenco di registri e i relativi valori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) per ottenere questa interfaccia. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) e [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) restituire anche questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugReference2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ottiene il [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura che descrive questo riferimento.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Imposta il valore del riferimento da una stringa.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Imposta il valore di questo riferimento da un altro riferimento.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera gli elementi figlio di questo riferimento.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ottiene l'elemento padre di questo riferimento.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ottiene il riferimento della Guida di riferimento più derivato.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ottiene i byte di memoria a cui fa riferimento questo riferimento.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ottiene un contesto in memoria per questo riferimento.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ottiene la dimensione, espressa in byte, della Guida di riferimento.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Imposta il tipo di riferimento.|
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Confronta questo riferimento con un altro.|

## <a name="remarks"></a>Note

> [!NOTE]
>  Questo uso di "property" non deve essere confuso con tale vale a dire una variabile membro di una classe, anche se un `IDebugReference2` può rappresentare tale entità.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rappresenta una proprietà, mentre `IDebugReference2` rappresenta un riferimento a una proprietà, in genere un riferimento a un oggetto del programma in fase di debug.

 La differenza principale tra una proprietà e un riferimento è che una proprietà fa riferimento a un'istanza denominata di un oggetto, mentre un riferimento è relativo a un'istanza senza nome. Ad esempio, una proprietà può fare riferimento a un oggetto nell'heap del programma da `"a.b"`. Un'altra proprietà può fare riferimento allo stesso oggetto come `"c.d"`. Il modo di fare riferimento a questa proprietà è necessario che `"a.b"` o `"c.d"` nell'ambito. Un riferimento all'oggetto stesso è senza nome; l'oggetto può essere indicato, purché la memoria per l'oggetto è valida.

 Un `IDebugProperty2` interfaccia può essere considerata un valore con un nome, un tipo e un indirizzo. Un `IDebugReference2`, da altra parte, può essere considerato un tipo e un indirizzo.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)