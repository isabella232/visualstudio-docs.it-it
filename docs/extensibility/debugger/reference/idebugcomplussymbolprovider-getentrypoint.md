---
title: IDebugComPlusSymbolProvider::GetEntryPoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetEntryPoint
- GetEntryPoint
ms.assetid: 9640e121-1da1-41f9-8e66-76efca36baf2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0325065838f63614f67560d97e3061fea50a2d29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905046"
---
# <a name="idebugcomplussymbolprovidergetentrypoint"></a>IDebugComPlusSymbolProvider::GetEntryPoint
Recupera il punto di ingresso dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetEntryPoint(  
   ULONG32         ulAppDomainID,  
   GUID            guidModule,  
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetEntryPoint(  
   uint              ulAppDomainID,  
   Guid              guidModule,  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulAppDomainID`  
 [in] Identificatore per il dominio dell'applicazione.  
  
 `guidModule`  
 [in] Identificatore univoco per il modulo.  
  
 `ppAddress`  
 [out] Restituisce il punto di ingresso rappresentato da un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetEntryPoint(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugAddress **ppAddress  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppAddress, IDebugAddress *));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetEntryPoint );  
  
    IfFalseGo( ppAddress, E_INVALIDARG );  
  
    *ppAddress = NULL;  
  
    IfFailGo( GetModule( idModule, &pModule) );  
  
    IfFailGo( pModule->GetEntryPoint( ppAddress ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetEntryPoint, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)