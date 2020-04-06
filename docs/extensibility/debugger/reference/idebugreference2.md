---
title: Proprietà IDebugReference2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720270"
---
# <a name="idebugreference2"></a>IDebugReference2
Questa interfaccia rappresenta un riferimento a una proprietà dello stack frame o a un'altra proprietà.

> [!NOTE]
> `IDebugReference2`è riservato per un utilizzo futuro `E_NOTIMPL`e tutti i relativi metodi devono restituire .

## <a name="syntax"></a>Sintassi

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per rappresentare un riferimento a un particolare tipo di valore. Ad esempio, il valore potrebbe essere un valore numerico come risultato di una valutazione dell'espressione, un contesto di memoria utilizzato per la visualizzazione della memoria o un elenco di registri e dei relativi valori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) per ottenere questa interfaccia. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) e [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) restituiscono anche questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugReference2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ottiene la struttura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) che descrive questo riferimento.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Imposta il valore di questo riferimento da una stringa.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Imposta il valore di questo riferimento da un altro riferimento.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera gli elementi figlio di questo riferimento.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ottiene l'elemento padre di questo riferimento.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ottiene il riferimento più derivato di questo riferimento.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ottiene i byte di memoria a cui fa riferimento questo riferimento.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ottiene un contesto di memoria per questo riferimento.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ottiene la dimensione, in byte, di questo riferimento.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Imposta questo tipo di riferimento.|
|[Confronta](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Confronta questo riferimento con un altro.|

## <a name="remarks"></a>Osservazioni

> [!NOTE]
> Questo utilizzo di "proprietà" non deve essere confuso con tale `IDebugReference2` significato una variabile membro di una classe, anche se un può rappresentare tale entità.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rappresenta una `IDebugReference2` proprietà, mentre rappresenta un riferimento a una proprietà, in genere un riferimento a un oggetto nel programma in fase di debug.

 La differenza principale tra una proprietà e un riferimento è che una proprietà fa riferimento a un'istanza denominata di un oggetto, mentre un riferimento fa riferimento a un'istanza senza nome. Ad esempio, una proprietà può fare riferimento a `"a.b"`un oggetto nell'heap del programma da . Un'altra proprietà può fare `"c.d"`riferimento allo stesso oggetto di . Il modo di fare riferimento `"a.b"` `"c.d"` a questa proprietà richiede che o essere nell'ambito. Un riferimento a questo stesso oggetto è senza nome; l'oggetto può essere definito fino a quando la memoria per tale oggetto è valida.

 Un'interfaccia `IDebugProperty2` può essere considerata come un valore con un nome, un tipo e un indirizzo. Un `IDebugReference2`, d'altra parte, può essere considerato come un tipo e un indirizzo.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
