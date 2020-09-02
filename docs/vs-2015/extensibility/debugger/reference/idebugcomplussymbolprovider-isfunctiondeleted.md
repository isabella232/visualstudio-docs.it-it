---
title: 'IDebugComPlusSymbolProvider:: IsFunctionDeleted | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionDeleted
ms.assetid: b276bd25-6658-4898-bc36-04ecdf92aa2f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 904eb54729298f29b98b5ae7dae0aa759a1119de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187223"
---
# <a name="idebugcomplussymbolproviderisfunctiondeleted"></a>IDebugComPlusSymbolProvider::IsFunctionDeleted
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina che la funzione in corrispondenza dell'indirizzo di debug specificato è stata eliminata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT IsFunctionDeleted(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsFunctionDeleted(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 in Indirizzo di debug rappresentato da un'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Questo indirizzo deve essere un METHOD_ADDRESS.  
  
## <a name="return-value"></a>Valore restituito  
 Se la funzione viene eliminata, restituisce `S_OK` . Se la funzione è esistente, restituisce `S_FALSE` .  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **CDebugSymbolProvider** che espone l'interfaccia [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::IsFunctionDeleted(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));  
  
    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionDeleted );  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsFunctionDeleted( address.addr.addr.addrMethod.tokMethod,  
                                     address.addr.addr.addrMethod.dwVersion,  
                                     address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates the function is not deleted  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::IsFunctionDeleted, hr );  
  
    if (!SUCCEEDED(hr))  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
