---
description: Questa interfaccia rappresenta una classe come tipo.
title: Interfaccia IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: aa6691a4606b6724eacd6386a569af02ceb2cddd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145146"
---
# <a name="idebugclassfield"></a>IDebugClassField
Questa interfaccia rappresenta una classe come tipo.

## <a name="syntax"></a>Sintassi

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa [l'interfaccia IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Questa interfaccia è una specializzazione che rappresenta un tipo di classe.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una serie di interfacce dispone di metodi che possono restituire questa interfaccia, tra cui [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). È anche possibile usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia [dall'interfaccia IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se il [metodo GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce il flag `FIELD_TYPE_CLASS` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nelle interfacce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) questa interfaccia implementa quanto segue:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Crea un enumeratore per le classi di base di questa classe.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Determina se nella classe è definita un'interfaccia specifica.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Crea un enumeratore per le classi annidate di questa classe.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Ottiene la classe che racchiude questa classe.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Crea un enumeratore per le interfacce implementate da questa classe.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Crea un enumeratore per i costruttori di questa classe.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Ottiene il nome dell'indicizzatore predefinito.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Crea un enumeratore per gli enumeratori annidati di questa classe.|

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
