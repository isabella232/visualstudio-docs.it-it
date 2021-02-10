---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be1ef047e01baaffe66e38503f0f7979fea74829
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953370"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia fornisce informazioni aggiuntive su un oggetto.

## <a name="syntax"></a>Sintassi

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per offrire supporto per gli alias e l'accesso alle informazioni sull'oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un'interfaccia [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) può ottenere questa interfaccia usando [QueryInterface](/cpp/atl/queryinterface). Inoltre, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Oltre ai metodi sull'interfaccia [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , l' `IDebugObject2` interfaccia implementa gli elementi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ottiene il campo o la variabile, se presente, che può eseguire il backup della proprietà rappresentata da questo oggetto.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ottiene l'oggetto di codice gestito che rappresenta il valore di questo oggetto.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crea un ID univoco per questo oggetto o restituisce un alias esistente.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ottiene l'alias associato a questo oggetto, se presente.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ottiene il tipo di questo oggetto.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se questo oggetto rappresenta i dati utente.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se lo stato di modifica e continuazione non è più valido.<br /><br /> Un analizzatore di espressioni personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL` ).|

## <a name="remarks"></a>Commenti
 Per una discussione sugli alias, vedere [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
