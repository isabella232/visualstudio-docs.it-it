---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a4838afc0d52ab60ae0a11de419393d68dfc06
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351338"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Questa interfaccia rappresenta un tipo di una variabile.

## <a name="syntax"></a>Sintassi

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai provider di simboli come classe di base per qualsiasi tipo che può essere determinato in fase di esecuzione. Si tratta di solo codice gestito.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia rappresenta una classe di base da cui possono essere derivate le interfacce più specializzate.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia non fornisce alcun metodo diverso da quelli ereditati da `IDebugField`.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)