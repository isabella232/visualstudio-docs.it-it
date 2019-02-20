---
title: IDebugComPlusSymbolProvider::UnloadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UnloadSymbols
- IDebugComPlusSymbolProvider::UnloadSymbols
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9374220e8cc9433d8420820d87e685175061a2b0
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413072"
---
# <a name="idebugcomplussymbolproviderunloadsymbols"></a>IDebugComPlusSymbolProvider::UnloadSymbols
Scarica i simboli di debug per il modulo specificato dalla memoria.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int UnloadSymbols(
    uint ulAppDomainID,
    Guid guidModule
);
```

#### <a name="parameters"></a>Parametri
`ulAppDomainID`  
[in] Identificatore del dominio dell'applicazione.

`guidModule`  
[in] Identificatore univoco del modulo.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.

```cpp
HRESULT CDebugSymbolProvider::UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pmodule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::UnloadSymbols );

#if DEBUG

    DebugVerifyModules();
#endif

    IfFailGo( GetModule( idModule, &pmodule ) );

#if DEBUG

    DebugVerifyModules();
#endif

    RemoveModule( pmodule );
    pmodule->Cleanup();

Error:
#if DEBUG

    DebugVerifyModules();
#endif

    METHOD_EXIT( CDebugSymbolProvider::UnloadSymbols, hr );

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
