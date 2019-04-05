---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62b84bd77038c7a17b65f764bd303d6a6372a52c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970307"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Estende la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia per abilitare il recupero delle interfacce di modulo e processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Implementata dai motori di debug e utilizzato dal [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pacchetto di Debug.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel `IDebugCodeContext2` interfaccia, questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera un riferimento all'interfaccia del modulo di debug.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera un riferimento all'interfaccia del processo di debug.|  
  
## <a name="remarks"></a>Note  
 Si tratta di un'interfaccia opzionale che in genere non deve essere implementato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
