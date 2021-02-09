---
title: 'IDebugBeforeSymbolSearchEvent2:: getmodulename | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetModuleName
- IDebugBeforeSymbolSearchEvent2::GetModuleName
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90baaadae88325754d41c76421a27d57220a533
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869999"
---
# <a name="idebugbeforesymbolsearchevent2getmodulename"></a>IDebugBeforeSymbolSearchEvent2::GetModuleName
Recupera il nome del modulo di cui è in corso il debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetModuleName(
    BSTR *pbstrModuleName
);
```

```csharp
public int GetModuleName (
    string pbstrModuleName
);
```

## <a name="parameters"></a>Parametri
`pbstrModuleName`\
out Nome del modulo.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **CDebugBeforeSymbolSearchEventBase** che espone l'interfaccia [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) .

```cpp
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)
{
    HRESULT hRes = E_FAIL;

    if (m_bstrModuleName)
    {

        *pbstrModuleName = SysAllocString( m_bstrModuleName);

        if (*pbstrModuleName)
        {
            hRes = S_OK;
        }
    }

    return ( hRes );
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)
