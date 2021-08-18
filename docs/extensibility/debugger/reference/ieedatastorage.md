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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1f8597a62f319247ca607d4b1f5221665f3de186
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152991"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Questa interfaccia rappresenta una matrice di byte.

## <a name="syntax"></a>Sintassi

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 L'analizzatore di espressioni (edizione Enterprise) implementa questa interfaccia per rappresentare una matrice di byte (usata dai visualizzatori di tipi per recuperare e modificare i dati tramite [l'interfaccia IPropertyProxyEESide).](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) L edizione Enterprise implementa in genere questa interfaccia per supportare i visualizzatori di tipi esterni.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Tutti i metodi `IPropertyProxyEESide` nell'interfaccia restituiscono questa interfaccia. Chiamare [GetPropertyProxy per](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) ottenere [l'interfaccia IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Chiamare [QueryInterface](/cpp/atl/queryinterface) su [un'interfaccia IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) per ottenere [l'interfaccia IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 `IEEDataStorage`L'interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera il numero specificato di byte di dati in un buffer fornito.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera il numero di byte di dati disponibili.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene usata da un visualizzatore di tipi per accedere ai dati di un oggetto specifico. I dati vengono considerati come una matrice di byte, consentendo al visualizzatore di tipi di modificarli in qualsiasi modo sia necessario per presentarlo all'utente.

 Un visualizzatore personalizzato può anche usare questa interfaccia, se lo si desidera, anche se in genere un visualizzatore personalizzato usa un'interfaccia personalizzata, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (per i dati orientati alle stringhe).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
