---
title: IDebugComPlusSymbolProvider::GetFunctionLineOffset | Microsoft Docs
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
- IDebugComPlusSymbolProvider::GetFunctionLineOffset
- GetFunctionLineOffset
ms.assetid: 51460f5a-4e98-427a-8315-27246e24fb61
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afdfc45388d3adaffdd37e7c0b38aeee712301de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528283"
---
# <a name="idebugcomplussymbolprovidergetfunctionlineoffset"></a>IDebugComPlusSymbolProvider::GetFunctionLineOffset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugComPlusSymbolProvider::GetFunctionLineOffset](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset).  
  
Recupera l'indirizzo all'interno di una funzione che rappresenta l'offset di riga specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetFunctionLineOffset(  
   IDebugAddress*  pAddress,   
   DWORD           dwLine,   
   IDebugAddress** ppNewAddress   
);  
```  
  
```csharp  
int GetFunctionLineOffset(  
   IDebugAddress     pAddress,   
   uint              dwLine,   
   out IDebugAddress ppNewAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in] Indirizzo che rappresenta una funzione.  
  
 `dwLine`  
 [in] Riga offset dall'inizio della funzione.  
  
 `ppNewAddress`  
 [out] Nuovo indirizzo che rappresenta l'offset dall'inizio della funzione di riga.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetFunctionLineOffset(  
    IDebugAddress *pAddress,  
    DWORD dwLine,  
    IDebugAddress **ppNewAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
    DWORD dwOffset;  
    CDebugAddress* paddr = NULL;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetFunctionLineOffset);  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    // Find the first offset for dwLine in the function  
  
    IfFailGo( pModule->GetFunctionLineOffset( address.addr.addr.addrMethod.tokMethod,  
              address.addr.addr.addrMethod.dwVersion,  
              dwLine,  
              &dwOffset ) );  
  
    // Create the new Address  
  
    address.addr.addr.addrMethod.dwOffset = dwOffset;  
    IfNullGo( paddr = new CDebugAddress(address), E_OUTOFMEMORY );  
    IfFailGo( paddr->QueryInterface( __uuidof(IDebugAddress),  
                                     (void**) ppNewAddress ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetFunctionLineOffset, hr);  
    RELEASE( paddr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

