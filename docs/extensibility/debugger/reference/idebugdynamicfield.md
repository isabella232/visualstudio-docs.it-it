---
title: Proprietà IDebugDynamicField . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731310"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Questa interfaccia rappresenta un tipo di una variabile.

## <a name="syntax"></a>Sintassi

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai provider di simboli come classe base per qualsiasi tipo che può essere determinato in fase di esecuzione. Questo è solo per il codice gestito.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia rappresenta una classe base da cui è possibile derivare interfacce più specializzate.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia non fornisce metodi diversi da `IDebugField`quelli ereditati da .

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
