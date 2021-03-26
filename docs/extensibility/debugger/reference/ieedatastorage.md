---
description: Questa interfaccia rappresenta una matrice di byte.
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f24921ec169c458a1b0b5ab1638c1379efd09da1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083362"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Questa interfaccia rappresenta una matrice di byte.

## <a name="syntax"></a>Sintassi

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni (EE) implementa questa interfaccia per rappresentare una matrice di byte (usata dai visualizzatori di tipo per recuperare e modificare i dati tramite l'interfaccia [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). L'EE implementa in genere questa interfaccia per supportare i visualizzatori di tipo esterno.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi sull' `IPropertyProxyEESide` interfaccia restituiscono tutti questa interfaccia. Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere l'interfaccia [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Chiamare [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) per ottenere l'interfaccia [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 L' `IEEDataStorage` interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera il numero specificato di byte di dati in un buffer fornito.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera il numero di byte di dati disponibili.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene utilizzata da un visualizzatore di tipi per accedere ai dati contenuti in un oggetto specifico. I dati vengono considerati come una matrice di byte, consentendo al Visualizzatore dei tipi di modificarlo in qualsiasi modo sia necessario per presentarlo all'utente.

 Un visualizzatore personalizzato può anche usare questa interfaccia, se si desidera, sebbene in genere un visualizzatore personalizzato usi un'interfaccia personalizzata, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (per i dati orientati alle stringhe).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
