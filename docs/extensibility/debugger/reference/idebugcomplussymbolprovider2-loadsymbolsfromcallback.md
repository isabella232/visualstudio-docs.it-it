---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- LoadSymbolsFromCallback
- IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
ms.assetid: 905315ba-8e9b-4889-b9da-98e1441950ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88964d7631681d779132738352acae356aae60a5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334667"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromcallback"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
Caricamenti di eseguire il debug dei simboli utilizzando il metodo di callback specificati.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT LoadSymbolsFromCallback(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    IUnknown* pUnkMetadataImport,
    IUnknown* pUnkCorDebugModule,
    BSTR      bstrModuleName,
    BSTR      bstrSymSearchPath,
    IUnknown* pCallback
);
```

```csharp
int LoadSymbolsFromCallback(
    uint   ulAppDomainID,
    Guid   guidModule,
    object pUnkMetadataImport,
    object pUnkCorDebugModule,
    string bstrModuleName,
    string bstrSymSearchPath,
    object pCallback
);
```

## <a name="parameters"></a>Parametri
`ulAppDomainID`\
[in] Identificatore del dominio dell'applicazione.

`guidModule`\
[in] Identificatore univoco del modulo.

`pUnkMetadataImport`\
[in] Oggetto che contiene i metadati del simbolo.

`pUnkCorDebugModule`\
[in] Oggetto che implementa il [ICorDebugModule (interfaccia)](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).

`bstrModuleName`\
[in] Nome del modulo.

`bstrSymSearchPath`\
[in] Percorso per cercare il file di simboli.

`pCallback`\
[in] Oggetto che rappresenta il metodo di callback.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaccia.

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromCallback(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IUnknown *pMetadataImport,
    IUnknown * _pCorModule,
    BSTR bstrModule,
    BSTR bstrSearchPath,
    IUnknown *pCallback)
{
    EMIT_TICK_COUNT("Entry -- Loading symbols for the following target:");
    USES_CONVERSION;
    EmitTickCount(W2A(bstrModule));

    CAutoLock Lock(this);

    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<ICorDebugModule> pCorModule;

    CModule* pmodule = NULL;
    CModule* pmoduleNew = NULL;
    bool fAlreadyLoaded = false;
    Module_ID idModule(ulAppDomainID, guidModule);
    bool fSymbolsLoaded = false;
    DWORD dwCurrentState = 0;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pMetadataImport, E_INVALIDARG );
    IfFalseGo( _pCorModule, E_INVALIDARG );

    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**)&pMetadata) );

    IfFailGo( _pCorModule->QueryInterface( IID_ICorDebugModule,
                                           (void**)&pCorModule) );

    ASSERT(guidModule != GUID_NULL);

    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;

    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );

    //
    // We are now allowing modules to be created that do not have SymReaders.
    // It is likely there are a number of corner cases being ignored
    // that will require knowledge of the hr result below.
    //
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;
    HRESULT hrLoad = pmoduleNew->Create( idModule,
                                         dwCurrentState,
                                         pMetadata,
                                         pCorModule,
                                         bstrModule,
                                         bstrSearchPath,
                                         pCallback );

    if (hrLoad == S_OK)
    {
        fSymbolsLoaded = true;
    }

    // Remove the old module
    if (fAlreadyLoaded)
    {
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));
        RemoveModule( pmodule );
    }

    IfFailGo( AddModule( pmoduleNew ) );

Error:

    RELEASE (pmodule);
    RELEASE (pmoduleNew);

    if (SUCCEEDED(hr) && !fSymbolsLoaded)
    {
        hr = hrLoad;
    }

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );
    EMIT_TICK_COUNT("Exit");
    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
