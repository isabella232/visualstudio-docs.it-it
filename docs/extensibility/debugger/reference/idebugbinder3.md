---
description: Questa interfaccia fornisce l'accesso a tipi, alias e servizi del visualizzatore personalizzato.
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f6be3b149450ec84158acc533230102fce5a67e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143610"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia fornisce l'accesso a tipi, alias e servizi del visualizzatore personalizzato.

## <a name="syntax"></a>Sintassi

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug implementa questa interfaccia per supportare alias, servizi del visualizzatore personalizzato e accesso alle informazioni sul tipo di oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un'interfaccia [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) ottiene questa interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Oltre ai metodi forniti dall'interfaccia [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , questa interfaccia implementa gli elementi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera un oggetto memoria che rappresenta la memoria a cui è associato questo oggetto.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera l'eccezione associata a questo oggetto (se presente),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera un alias dato il relativo nome.|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera una matrice di tutti gli alias per questo oggetto.|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Ottiene il numero di tipi di argomenti associati a questo oggetto.|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera un elenco di tipi di argomenti associati a questo oggetto.|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Ottiene un'interfaccia per un servizio del visualizzatore,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Converte il percorso di un oggetto o un indirizzo di memoria a 64 bit in un contesto di memoria.|

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
