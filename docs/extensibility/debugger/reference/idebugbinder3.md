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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 423bfa11073e2ed29474056098ad2a189e346113
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104352"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia fornisce l'accesso a tipi, alias e servizi del visualizzatore personalizzato.

## <a name="syntax"></a>Sintassi

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug implementa questa interfaccia per supportare gli alias, i servizi del visualizzatore personalizzato e l'accesso alle informazioni sul tipo di oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 [Un'interfaccia IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) ottiene questa interfaccia usando [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi forniti [dall'interfaccia IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) questa interfaccia implementa quanto segue:

|Metodo|Descrizione|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera un oggetto di memoria che rappresenta la memoria a cui è associato l'oggetto.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera l'eccezione associata a questo oggetto (se presente),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera un alias in base al nome,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera una matrice di tutti gli alias per questo oggetto .|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Ottiene il numero di tipi di argomento associati a questo oggetto .|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera un elenco di tipi di argomento associati a questo oggetto .|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Ottiene un'interfaccia a un servizio visualizzatore,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Converte un percorso di oggetto o un indirizzo di memoria a 64 bit in un contesto di memoria.|

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
