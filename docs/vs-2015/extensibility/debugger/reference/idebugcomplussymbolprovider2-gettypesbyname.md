---
title: IDebugComPlusSymbolProvider2::GetTypesByName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetTypesByName
- IDebugComPlusSymbolProvider2::GetTypesByName
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40eb29bab07e657d22cd9559fa53fa3ced2139ff
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "62540576"
---
# <a name="idebugcomplussymbolprovider2gettypesbyname"></a>IDebugComPlusSymbolProvider2::GetTypesByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un tipo in base al nome.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetTypesByName(  
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetTypesByName(  
   string               pszClassName,  
   enum_ NAME_MATCH     nameMatch,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszClassName`  
 [in] Nome del tipo.  
  
 `nameMatch`  
 [in] Seleziona il tipo di corrispondenza, ad esempio, distinzione maiuscole/minuscole. Un valore compreso il [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumerazione.  
  
 `ppEnum`  
 [out] Enumeratore che contiene il tipo o tipi con il nome specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Per i tipi generici, il nome per la ricerca per ' elenco\<int >' o ' elenco\<int, int >' sarebbe 'List'. Se vengono visualizzati in più moduli, tipi dello stesso nome di `ppEnum` parametro conterrà tutte le copie. È necessario utilizzare [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) e la distingue sulla base di `guidModule` parametro.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypesByName(  
    LPCOLESTR pszClassName,  
    NAME_MATCH nameMatch,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CModIter ModIter;  
    CModule* pmodule; // the iterator owns the reference  
    CFieldList listField;  
  
    ASSERT(IsValidWideStringPtr(pszClassName));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetTypesByName );  
  
    IfFalseGo( pszClassName && ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    hr = S_FALSE;  
  
    if ( nameMatch == nmCaseInsensitive)  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByNameCaseInsensitive( pszClassName,  
                    &listField,  
                    this ) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
    else  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByName( pszClassName,  
                                          &listField,  
                                          this) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
  
    // If the list is empty then no type  
    IfFalseGo( listField.GetCount(), E_FAIL );  
  
    // Create enumerator  
    IfFailGo( CreateEnumerator( ppEnum, &listField ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetTypesByName, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
