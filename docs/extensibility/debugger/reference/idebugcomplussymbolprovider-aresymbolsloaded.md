---
description: Determina se i simboli di debug vengono caricati per il modulo specificato in base all'identificatore di dominio dell'applicazione.
title: IDebugComPlusSymbolProvider::AreSymbolsLoaded | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77e28b608d5c0db1d26d83f2d9a5786877a3ba73
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145107"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Determina se i simboli di debug vengono caricati per il modulo specificato in base all'identificatore di dominio dell'applicazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT AreSymbolsLoaded (
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int AreSymbolsLoaded (
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Parametri
`ulAppDomainID`\
[in] Identificatore per il dominio dell'applicazione.

`guidModule`\
[in] Identificatore univoco per il modulo.

## <a name="return-value"></a>Valore restituito
Se i simboli di debug vengono caricati, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` .

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un oggetto **CDebugSymbolProvider** che espone [l'interfaccia IDebugComPlusSymbolProvider.](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

```cpp
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );

    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );
Error:

    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );
    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
