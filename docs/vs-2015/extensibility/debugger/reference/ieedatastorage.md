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
ms.openlocfilehash: a5d102a4a9cf7946e135ec8f6cdbff44015d3b47
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967314"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta una matrice di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni (EE) implementa questa interfaccia per rappresentare una matrice di byte (usato da visualizzatori di tipi per recuperare e modificare i dati tramite il [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface). In genere, l'analizzatore di Espressioni implementa questa interfaccia per supportare i visualizzatori di tipo esterno.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 I metodi sul `IPropertyProxyEESide` interfaccia tutte restituire questa interfaccia. Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere il [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaccia. Chiamare [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) in un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia per ottenere il [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Il `IEEDataStorage` interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera il numero specificato di byte di dati da un buffer specificato.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera il numero di byte di dati disponibili.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata da un visualizzatore di tipi per accedere a dati mantenuti da un oggetto specifico. I dati vengono considerati come una matrice di byte, consentendo il Visualizzatore di tipi di modificarla in base alle impostazioni è necessario presentare all'utente.  
  
 Un visualizzatore personalizzato possa anche usare questa interfaccia, se si desidera, sebbene in genere, un visualizzatore personalizzato utilizzerà un'interfaccia personalizzata, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) oppure [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (per i dati con nome orientato alla stringa).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualizzatore di tipi e visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
