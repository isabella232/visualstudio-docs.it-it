---
title: IDebugObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c179a4443c23373fb92adf522ee0af34acb19c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695263"
---
# <a name="idebugobject"></a>IDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta un oggetto creato dal Binder per incapsulare i valori dei simboli e delle espressioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia è la classe di base per tutti gli oggetti utilizzati dall'analizzatore di espressioni nelle espressioni analizzate. Viene restituito da una chiamata al metodo [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) . [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) ottiene le interfacce più specializzate da questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugObject` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Ottiene le dimensioni dell'oggetto.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Ottiene il valore dell'oggetto come una serie di byte consecutivi.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Imposta il valore dell'oggetto da una serie di byte consecutivi.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Imposta il valore di riferimento di questo oggetto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Ottiene il contesto della memoria che rappresenta l'indirizzo del valore dell'oggetto.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Verifica se l'oggetto è un riferimento null.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Confronta un oggetto con questo.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina se l'oggetto è di sola lettura.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina se l'oggetto è un proxy trasparente.|  
  
## <a name="remarks"></a>Osservazioni  
 L'analizzatore di espressioni usa questa interfaccia come classe di base per rappresentare gli oggetti in un albero di analisi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: EE. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione delle espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Associare](../../../extensibility/debugger/reference/idebugbinder-bind.md)
