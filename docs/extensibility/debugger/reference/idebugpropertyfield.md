---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c3376a6b8d6d269cac1f376e3f7f3f6f8a036f0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709629"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Questa interfaccia fornisce le funzioni che consentono di ottenere e impostare una proprietà.

## <a name="syntax"></a>Sintassi

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia nello stesso oggetto che implementa il [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Questa interfaccia è una specializzazione che supporta il concetto di proprietà in una classe.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Uso [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dalle [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaccia se la [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituzione del metodo `FIELD_KIND_PROP`.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfacce, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Ottiene il metodo che ottiene la proprietà.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Ottiene il metodo che imposta la proprietà.|

## <a name="remarks"></a>Note
 Una proprietà è un concetto di codice gestito e rappresenta un metodo che viene considerato come una variabile. Proprietà non esistono in C++ non gestito.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)