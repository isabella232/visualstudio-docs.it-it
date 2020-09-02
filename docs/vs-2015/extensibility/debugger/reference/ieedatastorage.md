---
title: IEEDataStorage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad398380c7c951b99e7d84283355ee9d31955173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704738"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta una matrice di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni (EE) implementa questa interfaccia per rappresentare una matrice di byte (usata dai visualizzatori di tipo per recuperare e modificare i dati tramite l'interfaccia [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). L'EE implementa in genere questa interfaccia per supportare i visualizzatori di tipo esterno.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 I metodi sull' `IPropertyProxyEESide` interfaccia restituiscono tutti questa interfaccia. Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere l'interfaccia [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Chiamare [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) su un'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) per ottenere l'interfaccia [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable  
 L' `IEEDataStorage` interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera il numero specificato di byte di dati in un buffer fornito.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera il numero di byte di dati disponibili.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia viene utilizzata da un visualizzatore di tipi per accedere ai dati contenuti in un oggetto specifico. I dati vengono considerati come una matrice di byte, consentendo al Visualizzatore dei tipi di modificarlo in qualsiasi modo sia necessario per presentarlo all'utente.  
  
 Un visualizzatore personalizzato può anche usare questa interfaccia, se si desidera, sebbene in genere un visualizzatore personalizzato usi un'interfaccia personalizzata, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (per i dati orientati alle stringhe).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
