---
description: Consente all'analizzatore di espressioni (edizione Enterprise) di specificare l'interfaccia di callback che verrà utilizzata dal motore del debugger per leggere le impostazioni delle metriche.
title: IDebugExpressionEvaluator2::SetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66d69dc119b23f06efebb9c8d87cf96792118bd1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138666"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Consente all'analizzatore di espressioni (edizione Enterprise) di specificare l'interfaccia di callback che verrà utilizzata dal motore del debugger per leggere le impostazioni delle metriche.

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
[in] Interfaccia da utilizzare per il callback delle impostazioni.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Questo metodo fornisce un'interfaccia al gestore di debug della sessione che un analizzatore di espressioni può usare per leggere le impostazioni delle metriche. Nel debug remoto è utile leggere le metriche nel [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] computer.

## <a name="example"></a>Esempio
Gli esempi seguenti illustrano come implementare questo metodo per un oggetto **CEE** che espone [l'interfaccia IDebugSettingsCallback2.](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

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

## <a name="see-also"></a>Vedi anche
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
