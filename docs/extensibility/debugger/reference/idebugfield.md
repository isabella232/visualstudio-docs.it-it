---
description: Questa interfaccia rappresenta un campo, ad esempio una descrizione di un simbolo o di un tipo.
title: Interfaccia IDebugField | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 24997c7dd1337c711f767a4af3e3dda454bb8459034801706abd68d006475c5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389813"
---
# <a name="idebugfield"></a>IDebugField
Questa interfaccia rappresenta un campo, ad esempio una descrizione di un simbolo o di un tipo.

## <a name="syntax"></a>Sintassi

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia come classe di base per tutti i campi.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia è la classe di base per tutti i campi. In base al valore restituito di [GetKind,](../../../extensibility/debugger/reference/idebugfield-getkind.md)questa interfaccia può restituire interfacce più specializzate usando [QueryInterface](/cpp/atl/queryinterface). Inoltre, molte interfacce restituiscono `IDebugField` oggetti da vari metodi.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugField` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ottiene informazioni visualizzabili sul simbolo o sul tipo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ottiene il tipo di campo.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ottiene il tipo di campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ottiene il contenitore del campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ottiene l'indirizzo del campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ottiene le dimensioni di un campo, in byte.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ottiene informazioni estese su un campo.|
|[Uguale](../../../extensibility/debugger/reference/idebugfield-equal.md)|Confronta due campi.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ottiene informazioni indipendenti dal tipo sul simbolo o sul tipo.|

## <a name="remarks"></a>Commenti
 Un tipo equivale a un linguaggio C `typedef` .

 Nell'esempio di linguaggio C++ seguente è `weather` un tipo di classe e e sono `sunny` `stormy` simboli:

```cpp
class weather;
weather sunny;
weather stormy;
```

 È possibile determinare se un campo rappresenta un simbolo o un tipo chiamando [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) ed esaminando il [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) risultato. Se il bit è impostato, il campo è un tipo e, se il bit è `FIELD_KIND_TYPE` `FIELD_KIND_SYMBOL` impostato, è un simbolo.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
