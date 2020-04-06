---
title: Proprietà IDebugObject2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726083"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Questa interfaccia fornisce informazioni aggiuntive su un oggetto.

## <a name="syntax"></a>Sintassi

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per offrire il supporto per gli alias e l'accesso alle informazioni sull'oggetto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia può ottenere questa interfaccia utilizzando [QueryInterface](/cpp/atl/queryinterface). Inoltre, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi sul [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) `IDebugObject2` interfaccia, l'interfaccia implementa quanto segue:In addition to the methods on the IDebugObject interface, the interface implements the following:

|Metodo|Descrizione|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ottiene il campo o la variabile (se presente) che può sostenere la proprietà rappresentata da questo oggetto.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ottiene l'oggetto di codice gestito che rappresenta il valore di questo oggetto.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crea un ID univoco per questo oggetto o restituisce un alias esistente.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ottiene l'alias associato a questo oggetto, se presente.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ottiene il tipo di questo oggetto.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se questo oggetto rappresenta i dati utente.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se lo stato Modifica e continuazione non è più valido.<br /><br /> Un analizzatore di espressioni personalizzate non implementa `E_NOTIMPL`questo metodo (deve sempre restituire ).|

## <a name="remarks"></a>Osservazioni
 Vedere [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) per una discussione sugli alias.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
