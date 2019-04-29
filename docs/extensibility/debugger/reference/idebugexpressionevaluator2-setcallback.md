---
title: IDebugExpressionEvaluator2::SetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d758d6c34563a2915e295514380cf07c847d86c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919743"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Abilita l'analizzatore di espressioni (EE) specificare l'interfaccia di callback che verrà utilizzato il motore di debugger (DE) per leggere le impostazioni di metrica.

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

#### <a name="parameters"></a>Parametri
`pCallback`

 [in] Interfaccia da utilizzare per il callback di impostazioni.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
Questo metodo fornisce un'interfaccia per il gestore di sessione di debug che un analizzatore di espressioni è possibile usare per leggere le impostazioni di metrica. È utile nel debug remoto per continuare a leggere le metriche di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] computer.

## <a name="example"></a>Esempio
Negli esempi seguenti viene illustrato come implementare questo metodo per un **CEE** oggetto che espone le [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) interfaccia.

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
