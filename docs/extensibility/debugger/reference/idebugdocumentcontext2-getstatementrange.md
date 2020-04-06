---
title: IDebugDocumentContext2::GetStatementRange Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731777"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Ottiene l'intervallo di istruzioni del file del contesto del documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
    TEXT_POSITION[] pBegPosition,
    TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametri
`pBegPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che viene compilata con la posizione iniziale. Impostare questo argomento su un valore null se queste informazioni non sono necessarie.

`pEndPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che viene compilata con la posizione finale. Impostare questo argomento su un valore null se queste informazioni non sono necessarie.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Un intervallo di istruzioni è l'intervallo delle righe che hanno contribuito al codice a cui fa riferimento questo contesto del documento.

Per ottenere l'intervallo di codice sorgente (inclusi i commenti) all'interno di questo contesto del documento, chiamare il [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) metodo.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CDebugContext` implementare questo metodo per un oggetto semplice che espone il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia. Questo esempio compila la posizione finale solo se la posizione iniziale non è un valore null.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
