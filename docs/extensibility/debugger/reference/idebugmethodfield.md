---
description: Questa interfaccia descrive un metodo.
title: IDebugMethodField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2c06cf4315bdd1595985ad7170fb7b46f1f33316
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126960"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Questa interfaccia descrive un metodo.

## <a name="syntax"></a>Sintassi

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa [l'interfaccia IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Questa interfaccia è una specializzazione che presenta un metodo .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare [QueryInterface per](/cpp/atl/queryinterface) ottenere questa interfaccia dall'interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_METHOD` . Inoltre, i metodi [GetPropertyGetter,](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)ed [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)restituiscono tutti l'interfaccia `IDebugMethodField` .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nelle interfacce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Crea un enumeratore per i parametri del metodo .|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Ottiene il puntatore "this" dell'oggetto contenente il metodo.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Crea un enumeratore per tutte le variabili locali del metodo.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Crea un enumeratore per le variabili locali selezionate del metodo.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Determina se è stato definito un attributo personalizzato specifico.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Crea un enumeratore per le variabili locali statiche del metodo.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Ottiene il contenitore globale del metodo.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Crea un enumeratore per il tipo di ogni argomento necessario per chiamare il metodo .|

## <a name="remarks"></a>Commenti
 Un metodo può contenere parametri e variabili locali.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
