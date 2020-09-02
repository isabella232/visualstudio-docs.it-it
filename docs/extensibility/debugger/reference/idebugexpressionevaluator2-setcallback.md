---
title: 'IDebugExpressionEvaluator2:: secallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 907fdaa928b3f84f6ff37490d5c54a9d48515053
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729341"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Consente all'analizzatore di espressioni di specificare l'interfaccia di callback che il motore del debugger (DE) utilizzerà per leggere le impostazioni della metrica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Parametri
`pCallback`\
in Interfaccia da utilizzare per il callback delle impostazioni.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Questo metodo fornisce un'interfaccia alla gestione del debug della sessione che può essere utilizzata da un analizzatore di espressioni per leggere le impostazioni della metrica. È utile nel debug remoto per leggere le metriche nel [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] computer.

## <a name="example"></a>Esempio
Negli esempi seguenti viene illustrato come implementare questo metodo per un oggetto **CEE** che espone l'interfaccia [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) .

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
