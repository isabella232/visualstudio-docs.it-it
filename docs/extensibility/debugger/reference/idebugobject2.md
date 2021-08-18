---
description: Questa interfaccia fornisce informazioni aggiuntive su un oggetto .
title: Interfaccia IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d3d18068b5ad9ef74a84a31366d7c90bdefc365c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153290"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Questa interfaccia fornisce informazioni aggiuntive su un oggetto .

## <a name="syntax"></a>Sintassi

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per offrire supporto per gli alias e l'accesso alle informazioni sull'oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 [Un'interfaccia IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) può ottenere questa interfaccia usando [QueryInterface.](/cpp/atl/queryinterface) GetObject [restituisce anche](../../../extensibility/debugger/reference/idebugalias-getobject.md) questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi [nell'interfaccia IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) l'interfaccia `IDebugObject2` implementa quanto segue:

|Metodo|Descrizione|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ottiene il campo o la variabile (se presente) che può essere di backup della proprietà rappresentata da questo oggetto .|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ottiene l'oggetto di codice gestito che rappresenta il valore di questo oggetto .|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crea un ID univoco per questo oggetto o restituisce un alias esistente.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ottiene l'alias associato a questo oggetto, se presente.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ottiene il tipo di questo oggetto .|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se questo oggetto rappresenta i dati utente.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se lo stato di Modifica e continuazione non è più valido.<br /><br /> Un analizzatore di espressioni personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL` ).|

## <a name="remarks"></a>Commenti
 Per informazioni sugli alias, vedere [IDebugAlias.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
