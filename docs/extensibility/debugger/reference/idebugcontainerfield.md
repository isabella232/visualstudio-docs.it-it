---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c93113f89c11e787a23cc57dfbebcce882125091
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922286"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Questa interfaccia rappresenta un simbolo o del tipo che è un contenitore per altri tipi o i simboli.

## <a name="syntax"></a>Sintassi

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia nello stesso oggetto che implementa il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia. Questa interfaccia è anche la classe base per tutte le interfacce che rappresentano i contenitori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Molti metodi sul numero di interfacce restituiscono questa interfaccia. Poiché si tratta di una classe di base per tutti i contenitori, interfacce più specializzate può ottenuto da questa interfaccia mediante [QueryInterface](/cpp/atl/queryinterface). Tali interfacce includono [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia, questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumeratore per i campi del contenitore.|

## <a name="remarks"></a>Note
 Matrici (contenitori per le variabili), classi (contenitori per i metodi e variabili) e i metodi (contenitori per i parametri e variabili locali) sono tutti esempi di contenitori.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)