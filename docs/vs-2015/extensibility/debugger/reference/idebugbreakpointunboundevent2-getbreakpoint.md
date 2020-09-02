---
title: 'IDebugBreakpointUnboundEvent2:: getbreakpoint | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
ms.assetid: ad73a207-b778-4dc5-b645-5ec668a63333
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11640da3bcf5ad25aced8bee6fd6d981d658a772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160058"
---
# <a name="idebugbreakpointunboundevent2getbreakpoint"></a>IDebugBreakpointUnboundEvent2::GetBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il punto di interruzione che è diventato non associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetBreakpoint(   
   IDebugBoundBreakpoint2** ppBP  
);  
```  
  
```csharp  
int GetBreakpoint(   
   out IDebugBoundBreakpoint2 ppBP  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppBP`  
 out Restituisce un oggetto [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) che rappresenta il punto di interruzione che è diventato non associato.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **CBreakpointUnboundDebugEventBase** che espone l'interfaccia [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) .  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetBreakpoint(  
    IDebugBoundBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pbp )  
        {  
            IDebugBoundBreakpoint2 *pibp;  
  
            hRes = m_pbp->QueryInterface(IID_IDebugBoundBreakpoint2, (void **) & pibp);  
  
            if ( S_OK == hRes )  
                *ppbp = pibp;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
