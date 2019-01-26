---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e9a883c99bb41decbe0bbb53d2a4c484e021c07
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929296"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Rappresenta un modificatore facoltativo di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenuto da un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta una classe o metodo.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera un elenco di modificatori facoltativi.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll