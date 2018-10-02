---
title: IDebugContainerField | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a911fe64f397a3a671787db00877a07f5ed1ccaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526549"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugContainerField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcontainerfield).  
  
Questa interfaccia rappresenta un simbolo o del tipo che è un contenitore per altri tipi o i simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia nello stesso oggetto che implementa il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia. Questa interfaccia è anche la classe base per tutte le interfacce che rappresentano i contenitori.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Molti metodi sul numero di interfacce restituiscono questa interfaccia. Poiché si tratta di una classe di base per tutti i contenitori, interfacce più specializzate può ottenuto da questa interfaccia mediante [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Tali interfacce includono [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia, questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumeratore per i campi del contenitore.|  
  
## <a name="remarks"></a>Note  
 Matrici (contenitori per le variabili), classi (contenitori per i metodi e variabili) e i metodi (contenitori per i parametri e variabili locali) sono tutti esempi di contenitori.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

