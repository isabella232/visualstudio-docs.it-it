---
title: IDebugProcessSecurity | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c3cfa0d8ef0f43b21ec2057b71b688b2d3ecb66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519343"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProcessSecurity](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity).  
  
`IDebugProcessSecurity` viene implementato da un fornitore di porte per avvisare l'utente che connessione al processo non sicura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProcessSecurity`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ottiene il nome utente dal fornitore della porta.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Un utente viene avvisato che la connessione al processo di debug è unsafe.|  
  
## <a name="remarks"></a>Note  
 Implementare questa interfaccia viene visualizzato un avviso e consentire all'utente di annullare se il processo a cui si sta associando può essere considerato non sicuro.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Porte](../../../extensibility/debugger/ports.md)   
 [Fornitori di porte](../../../extensibility/debugger/port-suppliers.md)   
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

