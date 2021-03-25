---
description: Questa interfaccia rappresenta un campo, ovvero una descrizione di un simbolo o di un tipo.
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c519ccfe70ba5685dec8230bf3e4fcb0eb768921
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073677"
---
# <a name="idebugfield"></a>IDebugField
Questa interfaccia rappresenta un campo, ovvero una descrizione di un simbolo o di un tipo.

## <a name="syntax"></a>Sintassi

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia come classe di base per tutti i campi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è la classe di base per tutti i campi. In base al valore restituito di [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md), questa interfaccia può restituire interfacce più specializzate tramite [QueryInterface](/cpp/atl/queryinterface). Molte interfacce restituiscono inoltre `IDebugField` oggetti di diversi metodi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugField` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ottiene le informazioni visualizzabili sul simbolo o sul tipo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ottiene il tipo di campo.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ottiene il tipo di campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ottiene il contenitore del campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ottiene l'indirizzo del campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ottiene le dimensioni in byte di un campo.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ottiene le informazioni estese su un campo.|
|[Uguale](../../../extensibility/debugger/reference/idebugfield-equal.md)|Confronta due campi.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ottiene informazioni indipendenti dal tipo sul simbolo o sul tipo.|

## <a name="remarks"></a>Commenti
 Un tipo è equivalente a un linguaggio C `typedef` .

 Nel seguente esempio di linguaggio C++, `weather` è un tipo di classe e `sunny` e `stormy` sono simboli:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Se un campo rappresenta un simbolo o un tipo può essere determinato chiamando [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) ed esaminando il risultato della [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) . Se il `FIELD_KIND_TYPE` bit è impostato, il campo è un tipo e se il `FIELD_KIND_SYMBOL` bit è impostato, si tratta di un simbolo.

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
