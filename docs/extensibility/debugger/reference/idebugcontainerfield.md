---
title: Proprietà IDebugContainerField . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733212"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Questa interfaccia rappresenta un simbolo o un tipo che è un contenitore per altri simboli o tipi.

## <a name="syntax"></a>Sintassi

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia. Questa interfaccia è anche la classe base per tutte le interfacce che rappresentano i contenitori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Molti metodi su molte interfacce restituiscono questa interfaccia. Poiché si tratta di una classe base per tutti i contenitori, è possibile ottenere interfacce più specializzate da questa interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface). Tali interfacce includono [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sul IDebugField interfaccia, questa interfaccia implementa il metodo seguente:In addition to the methods on the [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, this interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumeratore per i campi del contenitore.|

## <a name="remarks"></a>Osservazioni
 Le matrici (contenitori per le variabili), le classi (contenitori per metodi e variabili) e i metodi (contenitori per parametri e variabili locali) sono tutti esempi di contenitori.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
