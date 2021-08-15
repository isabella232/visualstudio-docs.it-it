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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d0345582e0429af045f085833be8b41158ca7ac12e3a5b1dda1721ed5b72d270
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239048"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Questa interfaccia rappresenta un simbolo o un tipo che è un contenitore per altri simboli o tipi.

## <a name="syntax"></a>Sintassi

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa [l'interfaccia IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Questa interfaccia è anche la classe di base per tutte le interfacce che rappresentano i contenitori.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Molti metodi in molte interfacce restituiscono questa interfaccia. Poiché si tratta di una classe di base per tutti i contenitori, è possibile ottenere interfacce più specializzate da questa interfaccia usando [QueryInterface.](/cpp/atl/queryinterface) Tali interfacce includono [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi [nell'interfaccia IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumeratore per i campi del contenitore.|

## <a name="remarks"></a>Commenti
 Matrici (contenitori per variabili), classi (contenitori per metodi e variabili) e metodi (contenitori per parametri e variabili locali) sono tutti esempi di contenitori.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
