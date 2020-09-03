---
title: 'IDebugBreakpointResolution2:: GetBreakpointType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b08e031b2a1e3fb5f7f024d43e36cad85eaa0cfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206074"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il tipo del punto di interruzione rappresentato da questa risoluzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```csharp  
int GetBreakpointType(   
   out enum_ BP_TYPE pBPType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pBPType`  
 out Restituisce un valore dall'enumerazione [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) che specifica il tipo di questo punto di interruzione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se il `bpResLocation` campo nella struttura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) associata non è valido.  
  
## <a name="remarks"></a>Osservazioni  
 Il punto di interruzione può essere un codice o un punto di interruzione dei dati, ad esempio.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un `CDebugBreakpointResolution` oggetto semplice che espone l'interfaccia [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .  
  
```  
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.    
      if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpResolutionInfo.bpResLocation.bpType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
