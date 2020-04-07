---
title: Proprietà IDebugField . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728749"
---
# <a name="idebugfield"></a>IDebugField
Questa interfaccia rappresenta un campo, ovvero una descrizione di un simbolo o di un tipo.

## <a name="syntax"></a>Sintassi

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia come classe base per tutti i campi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è la classe base per tutti i campi. In base al valore restituito di [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), questa interfaccia può restituire interfacce più specializzate utilizzando [QueryInterface](/cpp/atl/queryinterface). Inoltre, molte interfacce `IDebugField` restituiscono oggetti da vari metodi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugField`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ottiene informazioni visualizzabili sul simbolo o sul tipo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ottiene il tipo di campo.|
|[Tipo GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ottiene il tipo di campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ottiene il contenitore del campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ottiene l'indirizzo del campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ottiene le dimensioni di un campo, in byte.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ottiene informazioni estese su un campo.|
|[Uguale](../../../extensibility/debugger/reference/idebugfield-equal.md)|Confronta due campi.|
|[Informazioni su GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ottiene informazioni indipendenti dal tipo sul simbolo o sul tipo.|

## <a name="remarks"></a>Osservazioni
 Un tipo è equivalente `typedef`a un linguaggio C .

 Nell'esempio di linguaggio `weather` C, è un `sunny` `stormy` tipo di classe seguente e sono simboli:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Se un campo rappresenta un simbolo o un tipo può essere determinato chiamando [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) ed esaminando il [risultato della FIELD_KIND.](../../../extensibility/debugger/reference/field-kind.md) Se `FIELD_KIND_TYPE` il bit è impostato, il campo `FIELD_KIND_SYMBOL` è un tipo e, se il bit è impostato, è un simbolo.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
