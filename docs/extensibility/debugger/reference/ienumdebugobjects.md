---
title: Proprietà IEnumDebugObjects . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716261"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia.

## <a name="syntax"></a>Sintassi

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni implementa questa interfaccia per fornire set di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia. Si noti che non si tratta di un'enumerazione COM standard a causa della presenza del metodo [GetCount.](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia implementa i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera il set successivo di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti dall'enumerazione.|
|[Saltare](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Salta un numero specificato di voci.|
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Reimposta l'enumerazione sulla prima voce.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md) (Clona)|Recupera una copia dell'enumerazione corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera il numero di voci nell'enumerazione.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia consente a un motore di debug di enumerare un set di oggetti in una matrice.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
