---
description: Questa interfaccia rappresenta un riferimento a una stack frame o a un'altra proprietà.
title: Interfaccia IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: cb94ceba197e0006dee98392df01f836c45692c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029749"
---
# <a name="idebugreference2"></a>IDebugReference2
Questa interfaccia rappresenta un riferimento a una stack frame o a un'altra proprietà.

> [!NOTE]
> `IDebugReference2` è riservato per un uso futuro e tutti i relativi metodi devono restituire `E_NOTIMPL` .

## <a name="syntax"></a>Sintassi

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia per rappresentare un riferimento a un particolare tipo di valore. Ad esempio, il valore potrebbe essere un valore numerico come risultato di una valutazione dell'espressione, un contesto di memoria usato per la visualizzazione della memoria o un elenco di registri e dei relativi valori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) per ottenere questa interfaccia. [Anche GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) [e GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) restituiscono questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugReference2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ottiene la [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) che descrive questo riferimento.|
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

## <a name="remarks"></a>Commenti

> [!NOTE]
> Questo uso di "proprietà" non deve essere confuso con ciò che significa una variabile membro di una classe, anche se un può `IDebugReference2` rappresentare tale entità.

- [IDebugProperty2 rappresenta](../../../extensibility/debugger/reference/idebugproperty2.md) una proprietà, mentre rappresenta un riferimento a una proprietà, in genere un riferimento a un oggetto nel programma in fase `IDebugReference2` di debug.

 La differenza principale tra una proprietà e un riferimento è che una proprietà fa riferimento a un'istanza denominata di un oggetto, mentre un riferimento fa riferimento a un'istanza senza nome. Ad esempio, una proprietà può fare riferimento a un oggetto nell'heap del programma da `"a.b"` . Un'altra proprietà può fare riferimento allo stesso oggetto di `"c.d"` . Il modo in cui si fa riferimento a questa proprietà richiede `"a.b"` che o `"c.d"` sia nell'ambito. Un riferimento a questo stesso oggetto è senza nome. È possibile fare riferimento all'oggetto purché la memoria per tale oggetto sia valida.

 `IDebugProperty2`Un'interfaccia può essere pensata come un valore con un nome, un tipo e un indirizzo. Un `IDebugReference2` oggetto , d'altra parte, può essere pensato come un tipo e un indirizzo.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
