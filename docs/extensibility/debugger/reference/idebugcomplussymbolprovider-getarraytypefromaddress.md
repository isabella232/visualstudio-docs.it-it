---
title: IDebugComPlusSymbolProvider::GetArrayTypeFromAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetArrayTypeFromAddress
- IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
ms.assetid: cc0c53f1-8c0f-49fa-8dbe-bc155e9ce0ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 189bae80873e100be3371813add133982926edab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915230"
---
# <a name="idebugcomplussymbolprovidergetarraytypefromaddress"></a>IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
Recupera specificare le informazioni nella matrice specificata, data il relativo indirizzo di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[C++]  
HRESULT GetArrayTypeFromAddress(  
   IDebugAddress* pAddress,  
   BYTE*          pSig,  
   DWORD          dwSigLength,  
   IDebugField**  ppField  
);  
```  
  
```  
[C#]  
int GetArrayTypeFromAddress(  
   IDebugAddress   pAddress,  
   int[]           pSig,  
   uint            dwSigLength,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in] L'indirizzo di debug rappresentato da un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
 `pSig`  
 [in] Matrice da esaminare.  
  
 `dwSigLength`  
 [in] Lunghezza in byte del `pSig` matrice.  
  
 `ppField`  
 [out] Restituisce il tipo di matrice come rappresentato da un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetArrayTypeFromAddress(  
    IDebugAddress *pAddress,  
    BYTE *pSig,  
    DWORD dwSigLength,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
    CDEBUG_ADDRESS da;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    IfFailGo( pAddress->GetAddress(&da) );  
  
    if ( S_OK == hr )  
    {  
        IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );  
  
        IfFailGo( this->CreateType((const COR_SIGNATURE*)(pSig), dwSigLength, da.GetModule(), mdMethodDefNil, pGenScope, ppField) );  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress, hr );  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)