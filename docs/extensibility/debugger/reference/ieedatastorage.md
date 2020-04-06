---
title: Proprietà IEEDataStorage . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718184"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Questa interfaccia rappresenta una matrice di byte.

## <a name="syntax"></a>Sintassi

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni (EE) implementa questa interfaccia per rappresentare una matrice di byte (utilizzato dai visualizzatori di tipo per recuperare e modificare i dati tramite il [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaccia). L'eE implementa in genere questa interfaccia per supportare i visualizzatori di tipo esterno.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi `IPropertyProxyEESide` sull'interfaccia restituiscono tutti questa interfaccia. Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere l'interfaccia [IPropertyProxyEESide.Call](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) GetPropertyProxy to obtain the IPropertyProxyEESide interface. Chiamare [QueryInterface](/cpp/atl/queryinterface) su un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia per ottenere il [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 L'interfaccia `IEEDataStorage` implementa i seguenti metodi:

|Metodo|Descrizione|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera il numero specificato di byte di dati in un buffer fornito.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera il numero di byte di dati disponibili.|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia viene utilizzata da un visualizzatore di tipo per accedere ai dati contenuti da un oggetto specifico. I dati vengono trattati come una matrice di byte, consentendo al visualizzatore del tipo di modificarli in qualsiasi modo sia necessario presentarli all'utente.

 Un visualizzatore personalizzato può anche utilizzare questa interfaccia, se lo si desidera, anche se più in genere, un visualizzatore personalizzato utilizzerebbe un'interfaccia personalizzata, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (per i dati orientati alle stringhe).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
