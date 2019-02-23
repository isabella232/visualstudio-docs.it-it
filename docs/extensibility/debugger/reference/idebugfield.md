---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a036f6d08c6f88a30f8a8c9ab6d0d2e847065854
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682920"
---
# <a name="idebugfield"></a>IDebugField
Questa interfaccia rappresenta un campo, vale a dire, una descrizione di un simbolo o del tipo.

## <a name="syntax"></a>Sintassi

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia come classe base per tutti i campi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è la classe base per tutti i campi. In base al valore restituito del [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), questa interfaccia può restituire più specializzate interfacce usando [QueryInterface](/cpp/atl/queryinterface). Inoltre, molte delle interfacce restituiscono `IDebugField` oggetti da metodi diversi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugField`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ottiene visualizzabile informazioni relative al tipo o un simbolo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ottiene il tipo di campo.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ottiene il tipo di campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ottiene il contenitore del campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ottiene l'indirizzo del campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ottiene le dimensioni di un campo, in byte.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ottiene le informazioni relative a un campo estese.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Confronta due campi.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ottiene indipendenti dal tipo di informazioni sul simbolo o tipo.|

## <a name="remarks"></a>Note
 Un tipo è equivalente a un linguaggio C `typedef`.

 Nell'esempio seguente del linguaggio C++ `weather` è un tipo di classe, e `sunny` e `stormy` simboli:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Se un campo rappresenta un simbolo o tipo può essere determinato chiamando [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) ed esaminando il [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) risultato. Se il `FIELD_KIND_TYPE` bit viene impostato, il campo è un tipo e se il `FIELD_KIND_SYMBOL` bit viene impostato, è un simbolo.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)