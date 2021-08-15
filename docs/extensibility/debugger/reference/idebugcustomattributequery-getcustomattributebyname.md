---
description: Recupera un attributo personalizzato in base al nome.
title: IDebugCustomAttributeQuery::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery::GetCustomAttributeByName
- GetCustomAttributeByName
ms.assetid: 6779727c-d10a-4abe-9acd-d0a1eb0737e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96b5a910c7d09bec43885b57e55943376fe7b7babec13069351e10e2c57fbcab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121323690"
---
# <a name="idebugcustomattributequerygetcustomattributebyname"></a>IDebugCustomAttributeQuery::GetCustomAttributeByName
Recupera un attributo personalizzato in base al nome.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCustomAttributeByName(
    LPCOLESTR pszCustomAttributeName,
    BYTE*     ppBlob,
    DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
    string    pszCustomAttributeName,
    ref int[] ppBlob,
    out uint  pdwLen
);
```

## <a name="parameters"></a>Parametri
`pszCustomAttributeName`\
[in] Nome dell'attributo personalizzato.

`ppBlob`\
[in,out] Matrice di byte che contengono i dati dell'attributo personalizzato.

`pdwLen`\
[out] Lunghezza in byte del `ppBlob` parametro.

## <a name="return-value"></a>Valore restituito
Se l'esito è positivo, restituisce `S_OK`. Se l'attributo personalizzato non esiste, restituisce `S_FALSE` . In caso contrario, verrà restituito un codice di errore.

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un **oggetto CDebugClassFieldSymbol** che espone [l'interfaccia IDebugCustomAttributeQuery.](../../../extensibility/debugger/reference/idebugcustomattributequery.md)

```cpp
HRESULT CDebugClassFieldSymbol::GetCustomAttributeByName(
    LPCOLESTR pszCustomAttributeName,
    BYTE *pBlob,
    DWORD *pdwLen
)
{
    HRESULT hr = S_FALSE;
    CComPtr<IMetaDataImport> pMetadata;
    mdToken token = mdTokenNil;
    CComPtr<IDebugField> pField;
    CComPtr<IDebugCustomAttributeQuery> pCA;

    ASSERT(IsValidWideStringPtr(pszCustomAttributeName));
    ASSERT(IsValidWritePtr(pdwLen, ULONG*));

    METHOD_ENTRY( CDebugClassFieldSymbol::GetCustomAttributeByName );

    IfFalseGo( pszCustomAttributeName && pdwLen, E_INVALIDARG );

    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );

    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );
    IfFailGo( CDebugCustomAttribute::GetCustomAttributeByName( pMetadata,
              token,
              pszCustomAttributeName,
              pBlob,
              pdwLen ) );
Error:

    METHOD_EXIT( CDebugClassFieldSymbol::GetCustomAttributeByName, hr );
    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)
