---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1aa60d4bd187776d58e64a40fe4676f20c36140f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915682"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta un alias per una variabile numerico e consente un analizzatore di espressioni (EE) per ottenere il dominio dell'applicazione per l'alias.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dal motore di debug gestito (DE).  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaccia, questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera l'identificatore per il dominio applicazione.|  
  
## <a name="remarks"></a>Note  
 Un alias è un numero decimale in formato stringa seguita dal carattere #, ad esempio, & 1001.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: EE.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll