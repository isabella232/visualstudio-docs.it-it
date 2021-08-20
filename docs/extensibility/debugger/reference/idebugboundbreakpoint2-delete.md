---
description: Elimina il punto di interruzione.
title: IDebugBoundBreakpoint2::D elete | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::Delete
helpviewer_keywords:
- Delete method
- IDebugBoundBreakpoint2::Delete method
ms.assetid: 7088dc66-f24a-446f-a52a-397d02457a41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66ebbc0b34ba213dda63f7ddcdc02da9c693a4ec
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064747"
---
# <a name="idebugboundbreakpoint2delete"></a>IDebugBoundBreakpoint2::Delete
Elimina il punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Delete( 
    void 
);
```

```csharp
int Delete();
```

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce se lo stato dell'oggetto punto di interruzione associato è `E_BP_DELETED` impostato su (parte `BPS_DELETED` dell'BP_STATE enumerazione). [](../../../extensibility/debugger/reference/bp-state.md)

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto `CBoundBreakpoint` semplice che espone [l'interfaccia IDebugBoundBreakpoint2.](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

```
HRESULT CBoundBreakpoint::Delete(void)
{
    HRESULT hr;

    // Verify that the bound breakpoint has not been
    // deleted. If deleted, then return hr = E_BP_DELETED.
    if (m_state != BPS_DELETED)
    {
        m_pInterp->RemoveBreakpoint(m_sbstrDoc, this);

        // Change the state of the breakpoint to BPS_DELETED.
        m_state = BPS_DELETED;
        hr = S_OK;
    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
