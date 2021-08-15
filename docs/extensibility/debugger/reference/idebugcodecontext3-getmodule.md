---
description: Recupera un riferimento all'interfaccia del modulo di debug.
title: IDebugCodeContext3::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29330e94d57d81f9ddc2903b390006a022780e907441887612ee8629c1691784
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262204"
---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
Recupera un riferimento all'interfaccia del modulo di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetModule(
    IDebugModule2 **ppModule
);
```

```csharp
public int GetModule(
    out IDebugModule2 ppModule
);
```

## <a name="parameters"></a>Parametri
`ppModule`\
[out] Riferimento all'interfaccia del modulo di debug.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un **oggetto CDebugCodeContext** che espone l'interfaccia [IDebugBeforeSymbolSearchEvent2.](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)

```cpp
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;

    IfFalseGo( ppModule, E_INVALIDARG );
    *ppModule = NULL;

    IfFailGo( this->GetModule(&pModule) );
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
