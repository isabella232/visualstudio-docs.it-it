---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731310"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Questa interfaccia rappresenta un tipo di una variabile.

## <a name="syntax"></a>Sintassi

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai provider di simboli come classe di base per qualsiasi tipo che può essere determinato in fase di esecuzione. Si tratta solo di codice gestito.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia rappresenta una classe di base da cui è possibile derivare interfacce più specializzate.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Questa interfaccia non fornisce metodi diversi da quelli ereditati da `IDebugField` .

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
