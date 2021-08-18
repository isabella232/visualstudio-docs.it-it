---
description: Questa interfaccia rappresenta una raccolta di oggetti che implementano l'interfaccia IDebugObject.
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5521d5f6c825fd0ae5be96500d2e57af98746dba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103338"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Questa interfaccia rappresenta una raccolta di oggetti che implementano [l'interfaccia IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="syntax"></a>Sintassi

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per fornire set di oggetti che implementano [l'interfaccia IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md) Si noti che non si tratta di un'enumerazione COM standard a causa della presenza del [metodo GetCount.](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
- [GetElements restituisce](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera il set successivo di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) dall'enumerazione .|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignora un numero specificato di voci.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Reimposta l'enumerazione sulla prima voce.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera una copia dell'enumerazione corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera il numero di voci nell'enumerazione .|

## <a name="remarks"></a>Commenti
 Questa interfaccia consente a un motore di debug di enumerare un set di oggetti in una matrice.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
