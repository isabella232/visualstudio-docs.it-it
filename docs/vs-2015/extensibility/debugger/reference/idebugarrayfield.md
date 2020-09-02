---
title: IDebugArrayField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20d5df8df3e556f0908668b98a836cbedbbce47e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686997"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia descrive un simbolo o un tipo di matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa l'interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Questa interfaccia è una specializzazione che rappresenta oggetti matrice.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Usare [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per ottenere questa interfaccia dall'interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce il flag `FIELD_TYPE_ARRAY` .  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nelle interfacce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , questa interfaccia implementa gli elementi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Ottiene il numero di elementi nella matrice.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Ottiene il tipo di elemento nella matrice.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Ottiene l'ordine di priorità della matrice.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
