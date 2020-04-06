---
title: IDebugComPlusSymbolProvider2::GetTypesByName . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypesByName
- IDebugComPlusSymbolProvider2::GetTypesByName
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e7b85fb8d5b0e3256e172ff78bc3a5f660b69b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733426"
---
# <a name="idebugcomplussymbolprovider2gettypesbyname"></a>IDebugComPlusSymbolProvider2::GetTypesByName
Recupera un tipo dato il relativo nome.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="parameters"></a>Parametri
`pszClassName`\
[in] Nome del tipo.

`nameMatch`\
[in] Consente di selezionare il tipo di corrispondenza, ad esempio maiuscole/minuscole. Valore dell'enumerazione [NAME_MATCH.](../../../extensibility/debugger/reference/name-match.md)

`ppEnum`\
[fuori] Enumeratore che contiene il tipo o i tipi con il nome specificato.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Per i tipi generici, il\<nome da cercare 'List int>' o 'List\<int,int>' sarebbe 'List'. Se in più moduli vengono visualizzati `ppEnum` tipi con lo stesso nome, il parametro conterrà tutte le copie. È necessario utilizzare [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) e `guidModule` distinguere in base al parametro.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone il [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaccia.

```cpp
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
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
