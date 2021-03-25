---
description: Questa interfaccia rappresenta un simbolo o un tipo che è un contenitore per altri simboli o tipi.
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb3a50db80dc2acb075d1c6ec1fe585000468285
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077902"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Questa interfaccia rappresenta un simbolo o un tipo che è un contenitore per altri simboli o tipi.

## <a name="syntax"></a>Sintassi

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa l'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Questa interfaccia è anche la classe di base per tutte le interfacce che rappresentano i contenitori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Molti metodi su molte interfacce restituiscono questa interfaccia. Poiché si tratta di una classe di base per tutti i contenitori, è possibile ottenere interfacce più specializzate da questa interfaccia usando [QueryInterface](/cpp/atl/queryinterface). Tali interfacce includono [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sull'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumeratore per i campi del contenitore.|

## <a name="remarks"></a>Commenti
 Le matrici (contenitori per le variabili), le classi (contenitori per metodi e variabili) e i metodi (contenitori per parametri e variabili locali) sono tutti esempi di contenitori.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
