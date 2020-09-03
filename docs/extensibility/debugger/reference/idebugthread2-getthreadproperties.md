---
title: 'IDebugThread2:: GetThreadProperties | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadProperties
helpviewer_keywords:
- IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7f81f4b60dfda21ce59ad73076785a37b767873
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718697"
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
Ottiene le proprietà che descrivono il thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetThreadProperties (
    THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES*     ptp
);
```

```csharp
int GetThreadProperties (
    enum_THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES[]         ptp
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
in Combinazione di flag dell'enumerazione [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) che determina i campi da `ptp` compilare.

`ptp`\
[in, out] Struttura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) compilata con le proprietà del thread.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Le informazioni restituite da questo metodo vengono in genere visualizzate nella finestra debug **thread** .

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un `CProgram` oggetto semplice che implementa l'interfaccia [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

```cpp
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,
                                      THREADPROPERTIES *ptp)
{
    HRESULT hr = E_FAIL;

    // Check for valid argument.
    if (ptp)
    {
        // Create an array of buffers at ptp the size of the
        // THREADPROPERTIES structure and set all of the
        // buffers at ptp to 0.
        memset(ptp, 0, sizeof (THREADPROPERTIES));

        // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.
        if (dwFields & TPF_ID)
        {
            // Check for successful assignment of the current thread ID to
            // the dwThreadId of the passed THREADPROPERTIES.
            if (GetThreadId(&(ptp->dwThreadId)) == S_OK)
            {
                // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator
                // of the passed THREADPROPERTIES.
                ptp->dwFields |= TPF_ID;
            }
        }

        hr = S_OK;
    }
    else
        hr = E_INVALIDARG;

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
