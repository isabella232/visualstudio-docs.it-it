---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97e3165be9d478d08f4de7eb623de5b93fd3433a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330858"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia fornisce l'accesso a tipi, gli alias e servizi di visualizzatore personalizzato.

## <a name="syntax"></a>Sintassi

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug implementa questa interfaccia per supportare gli alias, servizi di visualizzatore personalizzato e accesso alle informazioni sul tipo di oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un' [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface ottiene questa interfaccia tramite [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi forniti dal [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia, questa interfaccia implementa quanto segue:

|Metodo|Descrizione|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera un oggetto di memoria che rappresenta la memoria a cui è associato questo oggetto.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera l'eccezione associata a questo oggetto (se presente),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera un alias in base al nome,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera una matrice di tutti gli alias per questo oggetto,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Ottiene il numero di tipi di argomento associato all'oggetto,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera un elenco di tipi di argomento associato all'oggetto,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Ottiene un'interfaccia per un servizio del visualizzatore,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Converte un percorso di oggetto o un indirizzo di memoria a 64 bit in un contesto in memoria.|

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)